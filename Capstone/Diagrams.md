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


# Sequence Diagram
```mermaid
sequenceDiagram
Alice ->> John: Hello John, how are you?
John -->> Alice: Great!
Alice -) John: See you later!
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
# System Design
```mermaid  
flowchart TD
	client["Client"]
	lb{Load Balancer}
    
	bs(Backend Service)
    fan-out(Fan-out Services)
    rs(Recommendation Service)
    as(Analysitcs Service)
    ars(Article Service)
    ac(Article Cache)
    afs(Article Feed Service)
    afc(Article Feed Cache)
    ns(Notification Service)
    ls(Log Service)
    ss(Search Service)
    
	cs(Collab Service)
    
    client --> lb
    lb --> bs
    bs --> fan-out
    fan-out --> as 
    fan-out --> ls
    fan-out --> ss
    fan-out --> rs
    bs --> ns
    bs --> ars
    ars --> ac
    bs --> afs
    afs --> afc
```

# Components
```mermaid
flowchart TD

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
	varchar username UK
	varchar name
	varchar email
	timestampz emailVerified
	text image
	
	integer follower_count
	integer[] followers FK
	integer following_count
	integer[] following FK

	text[] urls

	interests

	enum role "ADMIN, MANAGER, USER. default USER"
	varchar(255) bio
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
users ||--|{ verification_token : ""
users ||--|{ sessions : ""
users ||--|{ accounts : ""

articles {
	bigint article_id PK
	varchar article_name
	varchar relative_path
	bigint checksum
	timestampz created_at
	timestampz last_modified
	integer series FK
	real series_order
	string[] tags FK
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
	serial id PK
	string author FK
	integer articles
}
articles }|--|| series
```