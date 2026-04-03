# Team 6 Mist 4610 Group Project 1

## Team Name: 
71552 Group 6 

## Team Members:

1. Jesse Williams: [@jesnw](https://github.com/jeswn)
2. Tania Saputera: [@tas45087](https://github.com/tas45087)
3. Kate Nelms: [@ksn56497](https://github.com/ksn56497)
4. John Omolon: [@JohnOmolon](https://github.com/JohnOmolon)
5. Johan Jerry: [@johanjerry](https://github.com/johanjerry)

## Scenario Description :
Our data model follows an upscale boutique fitness studio with locations throughout Georgia and Florida. This fitness studio employs a subscription model with two tiers: a basic tier, with four classes a month, and an unlimited tier. This data model is designed to model accurate entity relationships and organize data. This is to manage multiple locations, track employees, monitor class attendance, optimize membership revenue, and manage class ratings. Therefore, providing business insights to optimize the fitness studio’s administration.  

## Data Model

<img width="1006" height="780" alt="image" src="https://github.com/user-attachments/assets/344b3c28-21ac-4cf2-b628-7274c2a39435" />

Our model is based on a hypothetical boutique fitness studio with locations throughout Georgia and Florida. The boutique operates on a membership subscription model, offering a basic or unlimited tier. The basic tier lets members attend only 4 classes per month, while the unlimited tier allows members to attend as many classes as they like. The goal of this data model is to organize the boutique’s operational data to maximize efficiency while managing multiple locations, employees, and trainers, monitoring class attendance, membership revenue, and ensuring member satisfaction.

Each studio location employs its own set of employees, trainers, and members, creating one-to-many relationships between entities: Location and Employees, Trainers, and Members. This allows management to analyze the number of employees and the distribution of members across different regions in GA and FL. Members are able to purchase subscription plans, which are stored in the Memberships entity, and define their membership tier as basic or unlimited, setting their monthly class limits and the price of their subscription.

Each class is taught by one trainer and takes place in one studio room; trainers and studio rooms can take on many classes. Our boutique offers multiple types of classes to members, such as Endurance, Strength, HIIT, and Power Circuits, and Slow Flow yoga classes. Each studio room has a max capacity of 30 participants to ensure the safety and satisfaction of our members and trainers during class. Additionally, each studio room contains equipment such as treadmills, rowers, dumbbells, and yoga mats, creating a one-to-many relationship between our Studio_Rooms and Equipment entities and helping our boutique to effectively keep tabs on the equipment and their associated costs for each studio room.

Members can attend many classes, and each class hosts many members, making our Attendance_Logs entity an associative table between Members and Classes. Attendance_Logs tracks the time that members check into class to determine if they check in on time or are late. The entity also tracks the attendance status of the class members who commit to, enforcing boutique policies such as penalties for members who “no-show” and tracking member participation trends. Members can also submit a review and a 1-5 star rating after attending a class, but only if their attendance status verifies they attended.

Revenue is tracked through the Payments entity, which records transactions associated with each member’s subscription. Additionally, the Referrals entity captures potential new customers through our boutique referral program for existing members, allowing managers to measure the effectiveness of the program strategy.

## Data Dictionary:
<img width="822" height="675" alt="image" src="https://github.com/user-attachments/assets/0a106d4d-3ba8-4908-8750-10a37b1f16a3" />
<img width="821" height="282" alt="image" src="https://github.com/user-attachments/assets/806cde52-eee6-4ec5-a3b7-7b9171d11b15" />
<img width="816" height="710" alt="image" src="https://github.com/user-attachments/assets/334295bc-caa4-48c7-beb8-072f835cb88d" />
<img width="816" height="332" alt="image" src="https://github.com/user-attachments/assets/21e083fb-cb21-4084-83df-9c737b7f1a62" />
<img width="812" height="321" alt="image" src="https://github.com/user-attachments/assets/f458eb8c-5862-4707-b88e-ed5cf5cefd21" />
<img width="817" height="640" alt="image" src="https://github.com/user-attachments/assets/24b17eb0-d58d-4ad8-abea-791927984094" />
<img width="817" height="576" alt="image" src="https://github.com/user-attachments/assets/7588816b-25c4-478c-a20e-0890fc402f7f" />
<img width="812" height="406" alt="image" src="https://github.com/user-attachments/assets/962101a8-7c7a-45c7-b990-fc34a6e62c99" />
<img width="811" height="687" alt="image" src="https://github.com/user-attachments/assets/d895b71d-3872-4ed5-9274-a08d07081ae2" />

## Ten Queries

Query 1: 

<img width="2050" height="440" alt="Screenshot 2026-04-03 175038" src="https://github.com/user-attachments/assets/ddcef1a0-8d26-4e40-8b22-f65a916b2a31" />

<img width="929" height="496" alt="Screenshot 2026-04-03 175148" src="https://github.com/user-attachments/assets/5efd5e12-a7dd-4fb6-a782-d12441852e50" />

**Explanation**: This query lists out each Studio Room ID, the total number of classes hosted in that room, and the total equipment value assigned to that room. It does this by joining the Equipment, Studio_Rooms, and Classes tables, then grouping the results by each Studio Room’s unique ID. The query also uses functions such as COUNT to calculate the number of classes held in each room and SUM with ROUND to calculate the total equipment value in each room. The HAVING clause limits the results to rooms that have hosted at least 3 classes.

**Business reasoning**: This query is useful to management because it helps identify which studio rooms are used most often and how much equipment value is tied to those rooms. By comparing room usage with equipment investment, managers can make better decisions about scheduling, maintenance, and resource allocation. It also helps them visualize whether the rooms with the heaviest class traffic are being supported with the appropriate level of equipment investment.

Query 2:

<img width="1175" height="222" alt="Screenshot 2026-04-03 175250" src="https://github.com/user-attachments/assets/57c469e5-eed8-4828-8a7f-8cd2ce8719f9" />

<img width="881" height="260" alt="Screenshot 2026-04-03 175318" src="https://github.com/user-attachments/assets/5e70e2f8-dcbb-4231-889e-439f8b4a636d" />

**Explanation**: This query displays each trainer’s first and last name, total revenue generated from membership payments from members assigned to that trainer, the average membership payment amount, and the total number of payments counted for that trainer. It does this by joining the Payments, Members, Location, and Trainers tables, then grouping the results by trainer name. The query uses functions including SUM to calculate total revenue, AVG to calculate the average payment amount, and COUNT to count the number of payments. The ROUND function is used to format the revenue and payment values to two decimal places. The HAVING clause limits the results to only trainers whose grouped payments total more than $500.

**Business reasoning**: This query displays which trainers contribute to the fitness studio’s revenue the most, acting as a way to measure ROI. It shows trainers who are high-value and are worth rewarding, because they contribute the most to the company’s success. 

Query 3:

<img width="1195" height="175" alt="Screenshot 2026-04-03 175746" src="https://github.com/user-attachments/assets/6d37f606-3bb2-477a-93b3-06664ecf7056" />

<img width="638" height="265" alt="Screenshot 2026-04-03 175814" src="https://github.com/user-attachments/assets/e11cb6b4-b847-4046-8fd5-48b4fa3b6c7d" />

**Explanation**: This query displays each class type, the total number of reviews it received, and the average rating for that class type, rounded to the nearest whole number. It does this by joining the Class Reviews, Attendance Logs, Classes, and Class Type tables to connect each review back to its corresponding class type. It then groups the results by classType so that all reviews for the same type of class are summarized together. It uses COUNT to calculate the total number of reviews and AVG with ROUND to calculate the rounded average rating. The HAVING clause ensures that only class types with at least 3 reviews are included, making the results more reliable and meaningful.

**Business reasoning**: This query is useful because it helps management identify which types of classes consistently receive strong feedback from members. By focusing only on class types with at least 3 reviews, the results are based on a more dependable amount of feedback rather than isolated opinions. This can help managers decide which class offerings should be expanded, promoted more heavily, or used as benchmarks for improving lower-performing class types.

Query 4:

<img width="1289" height="453" alt="Screenshot 2026-04-03 175853" src="https://github.com/user-attachments/assets/1cc54c8e-2149-48e9-a520-c54881e1fa01" />

**Explanation**: This query shows the count of attendants for each class start time offering who were late or no-shows, using ‘where’, ‘join’, and ‘time’ functions. This query uses the ‘time()’ functions to allow the group-by functions to group by all class offerings at that time, not just classes on particular dates.

**Business reasoning**: This shows when classes are more likely to have more attendants. This allows management to decide what times are more operationally efficient, and when to implement more classes in other rooms. 

Query 5: 

<img width="859" height="549" alt="Screenshot 2026-04-03 180106" src="https://github.com/user-attachments/assets/5972e3af-468a-442d-923d-ed21ea4ddf17" />

**Explanation**: This query shows the trainers with a higher average class rating than the average class rating for their location. This query uses a correlated subquery to match the trainers to the average class rating for their location. The query also utilizes multi-join and the ‘concat()’ function. 

**Business reasoning**: The query is useful because it shows managers who are above and beyond at their respective locations. This is a way to review performance and reward trainers who are exceeding expectations. 

Query 6:

<img width="887" height="617" alt="Screenshot 2026-04-03 180155" src="https://github.com/user-attachments/assets/0a0b210c-eb5a-4a73-a153-e847c52632bf" />

**Explanation**: This query uses the ‘case when’ function to categorize different members based on their satisfaction with classes that they attended. The ‘case when’ function separates any average rating above 4 to be ‘very satisfied,’ average ratings between 3 and 4 to be ‘satisfied,’ and anything below or equal to 3 to be ‘not satisfied.’ The query groups this information by the member’s name to see individuals satisfaction level. The query also utilizes multiple joins. 

**Business reasoning**: Determining which customers are very satisfied allows management to capitalize on their sentiment to increase referrals. This also allows follow-ups with unsatisfied customers to receive feedback to increase the efficiency and performance of trainers. 

Query 7: 

<img width="839" height="481" alt="Screenshot 2026-04-03 180657" src="https://github.com/user-attachments/assets/8fcae329-27bc-4665-a9bd-506be53e1f58" />

**Explanation**: This query displays each studio location along with the total number of class absences recorded as No-Show. It does this by joining the Location, Members, and Attendance_Logs tables so each member’s attendance record can be connected back to their studio location. The WHERE clause filters the results to include only attendance records marked as No-Show, so the query only considers members who were marked absent. The results are then grouped by locCity, and COUNT(*) is used to calculate the total number of no-shows for each location.

**Business reasoning**: This query is useful because it helps management identify which studio locations experience the highest levels of absenteeism. Locations with frequent no-shows may be facing issues such as poor class scheduling, inconvenient time slots, areas of weak member engagement, or necessary improvements in reminder systems. By spotting these trends, managers can improve scheduling decisions, strengthen attendance reminder processes, and better align class offerings with member demand to reduce wasted capacity.

Query 8: 

<img width="887" height="409" alt="Screenshot 2026-04-03 180717" src="https://github.com/user-attachments/assets/d9888f5e-efde-490e-987d-72c00323d24d" />

**Explanation**: This query calculates the number of referrals made by members and displays only members who have referred more than one new member. The results are ordered in descending order by the number of referrals.

**Business reasoning**: 
Managers are able to see which members are contributing the most to the referral program and the overall growth of the boutique. This information could be used to give benefits like discounted memberships to members who reach a certain number of referrals and evaluate the effectiveness of the referral program. Ordering the results from highest to lowest number of referrals allows managers to easily see the top contributors.

Query 9:

<img width="1012" height="803" alt="Screenshot 2026-04-03 182034" src="https://github.com/user-attachments/assets/3fa7ad07-b1ba-4bff-93fe-0cf36d23dcaa" />
<img width="799" height="546" alt="Screenshot 2026-04-03 182049" src="https://github.com/user-attachments/assets/d2b12693-f2b9-49f5-9225-af4021c9672f" />

**Explanation**: This query identifies trainers whose average class rating is higher than the overall average trainer rating across the entire studio system. It joins the Trainers, Classes, Attendance_Logs, and Class_Reviews tables so that each class review can be connected back to the trainer who taught the class. The query groups the results by trainer and calculates each trainer’s average rating using AVG(), rounded to two decimal places. The subquery first calculates the average rating for every trainer, then the outer query compares each trainer’s average against the average of those trainer averages. Only trainers whose rating exceeds the studio-wide average trainer rating are returned, and the results are sorted from highest to lowest rating.

**Business reasoning**: This query is useful because it helps management identify the trainers who consistently outperform the studio-wide standard for member satisfaction. These trainers can be recognized as top performers and used as role models for training best practices. It also gives management a reliable way to measure trainer performance relative to the organization as a whole instead of only within a single location.

Query 10:

<img width="1048" height="615" alt="Screenshot 2026-04-03 181014" src="https://github.com/user-attachments/assets/49fde3a9-e20f-4b52-b8cb-09e66ac8ab06" />

**Explanation**: This query finds members whose number of referrals is higher than the average number of referrals for their location. The query uses a correlated subquery to do this, matching the member’s location with the average number of referrals for their location. This query utilizes multiple joins and a left join in the subquery to achieve this. The purpose of the left join is to make sure that the average is fair and includes members who have made 0 referrals in the average calculation. 

**Business reasoning**: This query is managerially important by allowing management to see top referrals in locations and implement reward systems for members who are peak referrers. Also shows what locations need to implement loyalty systems to encourage more referrals. 

### Query Matrix

<img width="1077" height="640" alt="Screenshot 2026-04-03 182633" src="https://github.com/user-attachments/assets/0c62fd76-450c-4250-aca8-5727cf05c374" />

## Database Information:

Name of Database: ns_Sp26_71552_Group6

Additional Information: Each query listed above is marked in the database using stored procedures, which can be called using the following format: CALL Query_(#1-10) 

Ex. CALL Query_1;

