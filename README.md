The topic for the database is a travel agency. The goal is to simplify the agency's work. We have all the necessary entities that ensure that all important information is stored,
and predefined relationships between entities. Each entity describes a certain group of attributes. In the case of attributes, one represents the primary key that uniquely identifies our n-tuple
(one row of the table) that differs from other n-tuples. The attributes are determined according to the important information that we need to store about visitors, guides, destinations, etc.
Each entity should be well described. The idea is to make it easier to work with reservations because in this way we ensure that one tour guide is assigned to only one visitor in one day and we are sure that we will
have a sufficient number of tickets for our visitors. Tour guides have languages ​​that they speak while visitors need to say their native language. In this way, we enable their communication to be smooth. In order for
a visitor to come to a destination, he must first buy a ticket. However, one purchased ticket is only valid for one destination. In this way, we help the guides know where the visitor needs to go and whether they have
a valid ticket. In order for the agency to know what to keep and what to change, there are reviews that the visitor leaves. It is not their obligation, but they can leave more than one. In this way, the agency helps
them to work on their mistakes. The review is also linked to the destination so that we know which place the comment and rating is being left for. An important item is the reservation. In order for the 
visitor to come, they must first make a reservation and announce their arrival. The reservation includes a map, a tourist guide, etc., i.e. everything necessary for the visitor to be satisfied.

INFORMATION NEEDED TO UNDERSTAND THE PRINCIPLES OF MY DATABASE:
The travel agency keeps information about all tourist destinations, purchased tickets, visitors, tour guides, reservations, reviews and transportation to the destination. A tourist attraction/destination has its
own ID, short description, exact location, 1-5 star rating, name. A ticket has its own ID, price, discount. One ticket is valid for only one attraction, while multiple tickets are valid for one attraction.
There can be neither a ticket that is not valid for a destination nor a destination for which the ticket is not valid. The visitor has his/her ID, first name, last name, native language (the default value is Bosnian,
with a drop-down menu with a larger selection of languages), phone number. A visitor can buy multiple tickets at once, while only one visitor can buy one ticket. A visitor cannot be someone who has not purchased
a ticket, however, we do have tickets that have not yet been sold. After visiting the attraction, the visitor has the right to leave a review. A review has a rating of 1-5, a visitor's comment, and a review number.
One visitor has the right to leave multiple comments for a destination, while one identical review can only be made by one visitor. A visitor has the right to one tour guide. Tour guides have an ID, first name,
last name, foreign language they speak, and status of completed university. One tour guide is associated with several different destinations, while there can be several registered tour guides for one destination.
To avoid problems, there are reservations that clearly specify the date of the visitor's arrival and the flexibility of the staff. A reservation has an ID, date, time, and status (confirmed or rejected).
When a visitor decides to come, a reservation must be made. One identical reservation for that date can only be made by one visitor, and a visitor can only have 1 reservation for 1 day. The reservation is linked
to the visitor, but also to the tour guide and transportation. The visitor can also pay for transportation to the destination.

![ER dijagram](https://github.com/user-attachments/assets/8db04c66-5086-4985-9abb-3fc9bf0d2182)

The diagram shows all entities along with their attributes, and the relationships between the entities are shown. We will go through the relationships in detail
1. Destination-Valid-Ticket 1:N (one ticket is valid for one destination, and multiple tickets are valid for one destination) Both entities participate fully in the relationship.
2. Ticket-Buys-Visitor 1:N (one identical ticket can be purchased by one visitor, while a visitor can purchase multiple tickets). The ticket is not part of the reservation because it is assumed
3.  that the visitor will buy a ticket when he arrives, therefore a large number of tickets are provided
4. Visitor-Leaves-Review I:N (a visitor can leave multiple reviews, while only one visitor can leave a review) There cannot be a review that was not left by a visitor, therefore it fully participates
5.  in this relationship.
6. Destination-attached-tour guide N:M (there can be multiple tour guides at one destination, while one tour guide can be at multiple destinations)
7. Visitor-booked-reservation 1:1 (a visitor can have one reservation, and one visitor can have one reservation)
8. Reservation-located-tour guide 1:N (there can only be 1 tour guide within one reservation, while one tour guide can be in multiple reservations)
9. Reservation-located-transport 1:N (there can be one means of transport in one reservation, while one means of transport can be in multiple reservations)

![Relacioni model](https://github.com/user-attachments/assets/79bd9a19-a3ee-4cd4-a316-c3366fc2d139)

In the relational database model, each entity from the ER diagram becomes a separate table. The key principles for creating tables are:
Conversion rules:
1. Entities as tables
Each entity from the ER model becomes a table. The attributes of the entity become columns in that table, and the primary key (PK) of the entity becomes the primary key of the table.
Relations between entities:

One-to-many (1:N)
The primary key of the "one" side table becomes the foreign key (FK) in the "many" side table.

More-to-More (M:N)
This relation requires the creation of a new table. The new table contains the primary keys of both entities involved in the relation, which together form the composite primary key of the new table.

One-to-one (1:1)
The foreign key is usually placed in one of the entities, depending on the specifics of the application. If one entity is strictly dependent on another, the foreign key is added to the dependent entity.
