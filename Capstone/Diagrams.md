# Use Case
```mermaid
flowchart LR
r((Reader))
w((Writer))
p((Publisher))
a((Admin))
m((Moderator))

auth(sign up / login)

r --- auth
w --- auth

read(Read Article)

r --- read

follow(Follow Writer/Publisher)

r --- follow

write(Write Article)

subgraph Reading List
	direction TB
	createReadingList(Create Reading List)
	addToReadingList(Add Article to Reading List)
	removeToReadingList(Remove Article to Reading List)
end

getUser(Get user by id)

editp(Edit Profile)
 
subgraph Article Interactions
	direction TB
	like(Like Article)
	comment(Comment Article)
	share(Share Article)
end

subgraph Admin account management
	direction TB
	editAccount(Edit Account)
	deleteUser(Delete User)
	getUsers(Get the list of Users)
	banUser(Ban user)
end
 
subgraph Article management
	direction TB
	ediArticle(Edit Article)
	unpublishArticle(Unpublish Article)
	deleteArticle(Delete Article)
end 
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
	
	redis[(Redis Cache)]
	subgraph databases
	direction LR
	    neo4j[(Graph Database)]
	    sql[(Article Database)]
	end
    minio[(MINIO Object Storage)]
    
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
	api <--> minio
	api <--> redis
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
Account {
	string id PK  
	string userId FK  
	string type
	string provider  
	string providerAccountId  
	string refresh_token  
	string access_token  
	int expires_at  
	string token_type  
	string scope  
	string id_token  
	string session_state
}
User {
	string id PK
	string name
	string email
	timestamp emailVerified
	string image
}
Session {
	string id PK
	timestamp expires
	string sessionToken
	string userid FK
}
VerificationToken {
	string identifier
	string token UK
	timestamp expires
}
Article {
	string id PK
	string[] author FK
	string content
	string[] tags FK
}
Tag {
	string label
	int articleCount
}
```
# Sequence Diagram
```mermaid
sequenceDiagram
Alice ->> John: Hello John, how are you?
John -->> Alice: Great!
Alice -) John: See you later!
```