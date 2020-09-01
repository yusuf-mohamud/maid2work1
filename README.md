In most household, cleaning is an everyday thing. For some people, cleaning can be quite a difficult task because of the lack of time or just simple laziness. Maid2work, is an online website where people can offer private cleaning services or look for cleaning services.

Deployed site: www.example.com

Github repository: https://github.com/yusuf-mohamud/maid2work1

## Maid2Work
### Purpose
The purpose of this online marketplace is to help those who struggle with cleaning or just don't have time for it, find someone who is willing to clean their house for money. In this app, users will be able to provide or find services. 

### Functionality/ Features
Before the users can do anything meaningful, they will be required to sign up or login. Once logged in, users can update their profile, by writing about themselves, which language they speak, and what they can offer, and how much they are offering it for. They can then either, create a new service, or seek a service.

### Target audience
The target audience for maid2work includes studying or working young adults who don't have time to study. The predominent age group would be 18-50. However, this target audience is not strict.

### Tech Stack
1. Ruby on rails
2. HTML 5
3. CSS
4. Bulma
5. SCSS
6. JavaScript

### User story
1. As a user, you can sign up, login and logout.
2. As a user, you can view services
3. As a user, you can update profile, with information about yourself and profile picture.
4. As a user, you can create a new service
5. As a user you can purchase someone's service
6. As a user, you can connect to facebook

### High-level components (abstractions) in your app
Maid2work uses bulma as a css framework. It uses devise for authentication via email and uses omniauth for facebook authentication. In this website users will be able to post services or browse for services. The app has custom notifications such as "successfully logged in" and "signed out successfully", by using noty. Maid2work has image uploading capabilities for profile pictures and creating new service. Maid2work uses forms in the signup and login pages. 

### Third pary services
1. Heroku: for deployment
2. Github: for source control
3. Omniauth: for facebook authentication

### Describe your projects models in terms of the relationships (active record associations) they have with each other
Category
1. has_many :gigs

Gig
1. belongs_to :user
2. belongs_to :category
3. has_many :pricings
4. has_many :orders
5. has_many_attached :photos
6. has_rich_text :description
7. accepts_nested_attributes_for :pricings

Order
1. belongs_to :gig, required: false
2. belongs_to :buyer, class_name: "User"
3. belongs_to :seller, class_name: "User"

Pricing
1. belongs_to :gig

User
1. has_one_attached :avatar
2. has_many :gigs
3. has_many :buying_orders, foreign_key: "buyer_id", class_name: "Order"
4. has_many :selling_orders, foreign_key: "seller_id", class_name: "Order"

