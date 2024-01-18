# Use Case
```mermaid
flowchart LR
subgraph Users
	direction TB
	r((Reader))
	w((Writer))
	p((Publisher))
end

a((Admin))
m((Moderator))

subgraph Online Blogging Platform
	direction TB
	subgraph Auth
		direction TB
		signin(Sign In)
		signup(Sign Up)
		google(Google oauth)
		apple(apple oauth) 
	end
	
	search(Search User/Article/Publisher)

	subgraph User
		direction TB
		addWriters(Add Writers to Publisher)
		removeWriters(Remove Writers from Publisher)
		editProfile(Edit Profile)
		follow(Follow Writer/Publisher)
	end

	subgraph Article
		direction TB
		
		read(Read Article)
		
		subgraph Interactions
			direction TB
			like(Like Article)
			comment(Comment Article)
			share(Share Article)
		end
		
		subgraph Lists
			direction TB
			crl(Create Reading List)
			arl(Add Article to Reading List)
			rrl(Remove Article to Reading List)
		end
		
		analyse(Analyse Articles)
		write(Write Article)
		publish(Publish Article)
		unpublish(Unpublish Article)
		delete(Delete Article)
		
		subgraph Media
			direction TB
			getMedia(Get Media Files)
			upload(Upload File)
			remove(Remove File)
		end
		subgraph Series
			direction TB
			creates(Crate Series)
			pushs(Push Article to Series)
			pops(Pop Article to Series)
			reorders(Reorder Article to Series)
		end
	end

	subgraph Admin Account Management
		direction TB
		getAccounts(Get Accounts)
		getAccount(Get Account)
		editAccount(Edit Account)
		deleteAccount(Delete Account)
		banAccount(Ban Account)
	end
 
	subgraph Moderator Article management
		direction TB
		approveArticle(Approve Article)
		returnArticle(Return Article)
	end
end

Users --- Auth
Users --- search
Users --- editProfile

p --- addWriters
p --- removeWriters

r --- read
r --- follow
r --- Lists
r --- Interactions

w --- write
w --- publish
w --- unpublish
w --- analyse
w --- delete
w --- creates
w --- pushs
w --- pops
w --- reorders
w --- getMedia
w --- upload
w --- remove

a --- getAccounts
a --- getAccount
a --- editAccount
a --- deleteAccount
a --- banAccount

m --- approveArticle
m --- returnArticle
```
# Architecture
```mermaid
flowchart TD
	subgraph users
		a(Admin)
		cm(Content Manager)
		u(User)
	end
	
	subgraph client
		direction TB
		web(Web App)
		modile(modile App)
	end
	
	api(API)
	
	subgraph databases
		direction LR
	    graphdb[(Graph Database)]
	    db[(Database)]
	end
	
	cache[(Cache)]
    os[(Object Storage)]
    
    queue{Event Queue}
    
    ns(Notification Service)
    
    promoetheus(Promoetheus: Gather Metrics)
    grafana(Grafana: Visualize Metrics)
    logstash(Logstash: Gather Logs)
    
    elsaticsearch("Elsaticsearch for logs, mb later for searching in db")
    kibana(Kibana: Visualize Logs)
    
	users --> client
	client <--> api
	api <--> databases
	api <--> os
	api <--> cache
	api <--> queue
	queue --> ns
	api --> logstash
	logstash --> elsaticsearch
	elsaticsearch --> kibana
	api --> promoetheus
	promoetheus --> grafana
```
# Models
```mermaid
erDiagram
accounts {
	serial id PK "NOT NULL"  
	integer userId FK "NOT NULL"
	varchar type "NOT NULL"
	varchar provider "NOT NULL"
	varchar providerAccountId
	text refresh_token
	text access_token 
	bigint expires_at
	text token_type
	text scope
	text id_token
	text session_state
}
users {
	serial id PK
	varchar name
	varchar email
	timestampz emailVerified
	approved boolean
	
	text image
	varchar(255) bio

	integer follower_count
	integer following_count
	
	text[] urls
	
	enum role "ADMIN, MANAGER, PUBLISHER, USER. default USER"
	
	timestampz created_at
	timestampz last_modified
}
sessions {
	serial id PK
	timestamp expires "NOT NULL"
	varchar sessionToken "NOT NULL"
	integer userid FK "NOT NULL"
}
verification_token {
	text identifier "NOT NULL"
	text token UK "NOT NULL"
	timestampz expires "NOT NULL"
}
follow {
	integer follower_id PK, FK "Always User"
	integer following_id PK, FK
	enum follow_type "User, Publisher, Series"
}
articles {
	serial article_id PK
	
	integer publisher_id FK
	integer[] user_ids FK
	
	integer series_id FK
	integer series_order
	
	varchar article_name
	varchar relative_path
	bigint checksum
	
	text[] tag_ids FK
	integer[] reference FK

	integer like_count
	integer comment_count
	integer view_count

	timestampz created_at
	timestampz last_modified
}
article_version {
	bigint article_version_id PK
	bigint article_id FK
	string device_id "uuid"
	bigint version_number
	timestampz last_modified
}
article_block {
	bigint block_id PK
	bigint article_version_id FK
	bigint block_order
	enum block_type FK "NOT NULL; DEFAULT text"
	text content
}
tags {
	text label PK
	int articleCount
}
series {
	serial series_id PK
	text owner_id FK
	text label
	text image
	integer follower_count
	timestampz created_at
	timestampz last_modified
}
publishers {
	serial id PK
	
	varchar name
	varchar email
	approved boolean
	timestampz emailVerified
	text image
	
	text[] urls
	text[] tag_ids
	
	varchar(255) bio
	
	integer follower_count
	
	timestampz created_at
	timestampz last_modified
}
publisher_user {
	integer user_id PK, FK "NOT NULL"
	integer publisher_id PK, FK "NOT NULL"
	enum role_id "Manager, Writer Manager, Article Manager, Ad Manager"
}
lists {
	serial list_id PK
	integer user_id FK
	text label
	text image
	boolean visibility
	timestampz created_at
	timestampz last_modified
}
list_article {
	serial list_id PK, FK
	integer article_id PK, FK
	timestampz created_at
}
users ||--|{ verification_token : "Email/Passwordless login"
users ||--|{ sessions : "Database session management"
users ||--|{ accounts : "saves tokens retrieved from the provider"

users }o--o{ articles : articles_users_ids_fkey
articles |o--o{ articles : articles_reference_fkey
articles ||--|{ article_version : article_version_article_id_fkey
article_version ||--|{ article_block : article_version_article_block_id_fkey

users |o--|{ lists : list_user_id_fkey
lists }|--|{ list_article: list_article_list_id_fkey
list_article }o--o{ articles: list_article_article_id_fkey

users }o--o{ series: series_owner_id_fkey
publishers }o--o{ series: series_owner_id_fkey
series }|--|| articles : article_series_id_fkey

users }o--o{ follow : follow_follower_id_fkey
users }o--o{ follow : follow_following_id_type_users_fkey
follow }o--o{ series : follow_following_id_type_series_fkey
follow }o--o{ publishers : follow_following_id_type_publishers_fkey

users }o--o{ publisher_user : publisher_user_user_id_fkey
publisher_user }o--o{ publishers : publisher_user_publisher_id_fkey
publishers |o--o{ articles : articles_publisher_id_fkey

users }|--|{ tags : users_tag_ids_fkey
publishers }|--|{ tags : publishers_tag_ids_fkey
articles }|--|{ tags : articles_tag_ids_fkey
```