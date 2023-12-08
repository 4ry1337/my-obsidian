# Name: Digital Creators HUB

- [ ] token experation in db, creation, refresh
- [ ] other api's
- [ ] [GetReal](https://basecamp.com/gettingreal)
- [ ] 

## App
Digital Creators HUB is a web application that allows digital creators, such as designers, developers, writers, and photographers, to showcase their work, connect with potential clients and collaborators, and share their thoughts and ideas with the wider community.

### Objectives:

- To provide a platform for creators to share and showcase their works.
- To offer a community for creators to connect and engage with others.
- To allow creators to get feedback and appreciation for their work.
- To offer a simple and user-friendly platform.
- To help creators build a portfolio and online presence.
- To provide a space for creativity and self-expression.
- To enable creators to share their works with a wider audience.
- To create a sense of belonging and support for creators within the community.
- To provide a space for users to discover and appreciate creative works from a diverse range of creators.
- To establish the Digital Creator as a go-to destination for creators looking to share and showcase their work.

### Features:

- **User authentication and authorization**: Users will be able to create an account and log in to the Digital Creator. They will also be able to edit their profile information and control the privacy of their works.
- **Posting and sharing works**: Users will be able to create new posts for their works and specify categories such as art, music, writing, or photography. They will also be able to attach images or files to their posts and add tags to make it easier for others to find their work.
	- Tabs: Users can create sections/tabs in their profile with specific type of digital product.
	- Posts: Users can create a posts to display their past projects and creations, as well as categorize them by tags and categories. Posts will include options for adding titles, descriptions, and links for each project. Adding blogs about the process of creation.
- **Viewing and commenting on works**: Users will be able to browse and search for works by other users and leave comments on them. They will also be able to "like" and "favorite" works that they appreciate.  
- **Notifications and activity feed**: Users will receive notifications when their works are liked or commented on, and they will be able to view an activity feed that shows the latest interactions on their works.  
- **Admin panel**: An admin panel will be provided to allow site administrators to moderate the content on the Digital Creator and manage user accounts.

### Benefits:
- Provides a platform for creators to share and showcase their works: Creators can use the Digital Creator to share their art, music, writing, and other creative works with a wider audience. This can help them gain exposure and feedback for their work.
- Offers a community for creators to connect and engage with others: The Digital Creator offers a community of creators who can connect with each other and share their works. This can provide a sense of belonging and support for creators who may otherwise feel isolated.  
- Allows creators to get feedback and appreciation for their work: The ability to post works and receive comments and likes from others can be a great source of motivation and validation for creators.
- Offers a simple and user-friendly platform: The Digital Creator will be designed with ease of use in mind, making it accessible to creators of all skill levels.  
- Helps creators build a portfolio and online presence: Creators can use the Digital Creator to build a portfolio of their works and establish an online presence. This can be useful for those looking to further their careers in the creative field.  
- Provides a space for creativity and self-expression: The Digital Creator offers a space for users to express themselves and share their creativity with others. This can be a valuable outlet for those who have a passion for creating.
- The use of the tech stack of MERN, Redux, Tailwind CSS, and Chakra UI will provide a reliable and scalable foundation for the app. The use of TypeScript as the programming language will ensure strong type checking and support for object-oriented programming principles.

### Market Analysis

Artstation, DeviantArt, and Dribble are all online communities for creative professionals and enthusiasts to share and discover creative works. They are similar to the Digital Creator in that they all provide a platform for users to showcase their art, design, and other creative works.

However, Artstation, DeviantArt, and Dribble all have a focus on a specific creative field, such as visual art or design, whereas the Digital Creator is intended to be a more general platform for all types of creative works.

## Architecture
programming language: typescript

### Frontend
Single-Page Application

Framework: React
State Manger: Redux
CSS:
	framework: Tailwind-css
	library: chakra-ui
feature-first

### Backend
Server: Node.js
Server framework: Express.js
Authorization: JSON Web Token and Passport.js
Database: MongoDB
category-first


## Layout

- Home page
    - Hero image or video
    - Search bar
    - Grid of featured works
    - Links to popular categories
    - Newsletter sign-up form
- Category pages
    - Grid of works within the category
    - Search bar
    - Links to popular tags
- Work detail page
    - Hero image or video
    - Title and description
    - Grid of related works
    - Comments section
    - Links to share on social media
- User profile page
    - Bio
    - Grid of user's works
    - Grid of sections
    - List of followers
    - Links to social media accounts
    - Contact form
- Admin panel
    - Content moderation tools
    - User account management
    - Reporting tools

- Components:
	- About: This could be a link to a page that provides information about the Digital Creator, including its purpose and mission.
	- Contact: This could be a link to a contact form or a page with contact information for the Digital Creator team.
	- [[Terms of Service]]: This could be a link to a page that outlines the terms of service for using the Digital Creator.
	- [[Privacy Policy]]: This could be a link to a page that outlines the privacy policy for the Digital Creator, including how user data is collected and used.
	- FAQ: This could be a link to a page that provides answers to common questions about the Digital Creator.
	- Social media: Links to the Digital Creator's social media accounts, such as Facebook, Twitter, and Instagram, could be included in the footer.

![[Web Structure.png]]
## Design
Themes
- Dark
- Light
- Custom (feature in future)

[Figma](https://www.figma.com/file/OxnpbNmFFq79gTD3SVinAd/Untitled?t=4zoNAInb3lwamjbK-6)