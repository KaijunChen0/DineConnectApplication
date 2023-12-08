# Welcome to *DineConnect*!

**DineConnect** is a restaurant discovery app that provides convenient restaurant search, personalized recommendations, and location-based suggestions for food enthusiasts who are unhappy with the inconvenience of sifting through various dining options, the lack of personalized restaurant suggestions, and the limitations of current restaurant search methods.

## Features and Capabilities

### Feature 1: Tailor Restaurant Recommendations

When users open our website, our application will offer suggestions for good
restaurants located near their current location. This feature serves as a quick
guide to users, especially when they are not familiar with the area. Whether user are exploring their nearby or having special requests, our suggestions help them to make informed decisions swiftly.

### Feature 2: Interactive Restaurant Engagement

 - Restaurant Reviews

	Users can share their dining experiences by posting detailed restaurant reviews. Whether they want to praise exceptional service or provide constructive 		 feedback, their reviews help fellow diners make informed choices.

 - Check-Ins

	Users can check in at the restaurants they visit, allowing them to share their
real-time dining adventures with friends and followers. Checking in also helps users keep track of their culinary explorations.

 - Restaurant Promotion Events

	For restaurant owners and managers, we provide a platform to create and
promote special events such as happy hours, themed nights, and exclusive menus.
Users can easily discover these events and plan their visits accordingly.

 - User-Generated Tips

	Our community-driven approach allows users to share insider tips and recommendations with other customers. Whether it's a hidden gem on the menu or the best time to visit, these tips enhance the overall dining experience for everyone.

## Data sources
[Kaggle Yelp DataSet](https://www.kaggle.com/datasets/yelp-dataset/yelp-dataset)
> **How to process the data:** To process the data efficiently, start by reading the JSON files using Python and loading them into a Pandas DataFrame. Perform data manipulation, such as filtering and cleaning, and randomly sample 50k records, including associated information. Save the processed data as CSV files for further analysis and application use. This approach optimizes data handling while retaining essential information.

## DineConnect Database UML Design

```mermaid
classDiagram
Users  "0..1"  o--  "*"  Reviews
Users  "0..1"  o--  "*"  Checkins
Users  "0..1"  o--  "*"  Tips
Businesses  "1"  *--  "*"  Reviews
Businesses  "0..1"  o--  "*"  Checkins
Businesses  "1"  *--  "*"  Tips
Businesses  "1"  <|--  "0..1"  BusinessByAppointment
Businesses  "1"  <|--  "0..1"  BusinessByAttire
Businesses  "1"  <|--  "0..1"  BusinessByAlchholType
Businesses  "1"  *--  "*"  Promotions
Cities  "1"  o--  "*"  Businesses
AttireType  *--  BusinessByAttire
AlcoholType  *--  BusinessByAlchholType

class Users
Users  :  UserId string  -pk
Users  :  username string
Users  :  YelpingSince datetime

class Reviews
Reviews  :  ReviewId string  -pk
Reviews  :  Comment string
Reviews  :  CreatedTime datetime
Reviews  :  CommentStars decimal
Reviews  :  BusinessId string  -fk
Reviews  :  UserId string  -fk

class Checkins
Checkins  :  CheckinId integer  -pk
Checkins  :  CheckinTime datetime
Checkins  :  UserId string  -fk
Checkins  :  BusinessId string  -fk

class Tips
Tips  :  TipId integer  -pk
Tips  :  Text string
Tips  :  CreatedTime datetime
Tips  :  UserId string  -fk
Tips  :  BusinessId string  -fk

class Cities
Cities  :  PostalCode string  -pk
Cities  :  City string
Cities  :  State string

class BusinessByAppointment
BusinessByAppointment  :  BusinessId string  -pk
BusinessByAppointment  :  ByAppointmentOnly boolean

class BusinessByAttire
BusinessByAttire  :  BusinessId string  -pk
BusinessByAttire  :  AttireType enum 

class BusinessByAlchholType
BusinessByAlchholType  :  BusinessId string  -pk
BusinessByAlchholType  :  AlcoholType enum

class Promotions
Promotions  :  PromotionId integer  -pk
Promotions  :  BusinessId string  -fk
Promotions  :  StartTime datetime
Promotions  :  EndTime datetime
Promotions  :  Event string

class Businesses
Businesses  :  BusinessId string  -pk
Businesses  :  BusinessName string
Businesses  :  BusinessStars decimal
Businesses  :  Longitude decimal
Businesses  :  Latitude decimal
Businesses  :  Address string
Businesses  :  MondayListedHours string
Businesses  :  TuesdayListedHours string
Businesses  :  WednesdayListedHours string
Businesses  :  ThursdayListedHours string
Businesses  :  FridayListedHours string
Businesses  :  SaturdayListedHours string
Businesses  :  SundayListedHours string
Businesses  :  PostalCode string

class  AttireType{
<<enumeration>>
CASUAL
DRESSY
FORMAL
}

class  AlcoholType{
<<enumeration>>
NONE
BEER_AND_WINE
FULL_BAR
}
```

## Video Demo
<div>
    <a href="https://www.loom.com/share/4e917c053d724db8a78fcef6bdee71ff">
      <p>DineConnect Demo - December 2023 - Watch Video</p>
    </a>
    <a href="https://www.loom.com/share/4e917c053d724db8a78fcef6bdee71ff">
      <img style="max-width:300px;" src="https://cdn.loom.com/sessions/thumbnails/4e917c053d724db8a78fcef6bdee71ff-with-play.gif">
    </a>
  </div>
