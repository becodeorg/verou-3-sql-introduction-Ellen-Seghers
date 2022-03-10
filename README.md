# SQL introduction

- Repository: `n/a` (so no repo)
- Type of Challenge: `Learning`
- Duration: `1 day`
- Team challenge : `solo`

## The Mission

### 🌱 Must-have features

> You'll find that a lot of these tasks can be performed with MySQL queries and through your database manager. In time, you'll discover what works best for each task. A `*` means you should use a query for this.

1. Get familiar with [the basics](./SQL-basics.md) and set up a database 
#CREATE DATABASE IF NOT EXISTS `verou-3`
2. Make the following tables and populate them with some dummy data (have at least two entries for every table) 
    - groups: id, name, location, start_date, max_participants
    - learners: id, name, email, active
    - coaches: id, name

    DROP TABLE IF EXISTS `coaches`;
    CREATE TABLE IF NOT EXISTS `coaches` (
   `id` int(11) NOT NULL AUTO_INCREMENT,
   `name` varchar(255) NOT NULL,
   PRIMARY KEY (`id`)
   ) ENGINE=MyISAM AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4;

   INSERT INTO `coaches` (`id`, `name`) VALUES
   (1, 'Azog'),
   (5, 'Gorbag'),
   (2, 'Bolg');


   DROP TABLE IF EXISTS `groups`;
   CREATE TABLE IF NOT EXISTS `groups` (
   `id` int(11) NOT NULL AUTO_INCREMENT,
   `name` varchar(255) NOT NULL,
   `location` varchar(255) NOT NULL,
   `start_date` date NOT NULL,
   `max_participants` int(30) NOT NULL,
   PRIMARY KEY (`id`)
   ) ENGINE=MyISAM AUTO_INCREMENT=12 DEFAULT CHARSET=utf8mb4;

   INSERT INTO `groups` (`id`, `name`, `location`, `start_date`, `max_participants`) VALUES
   (1, 'Bilbo', 'Shire', '2021-09-22', 30),
   (11, 'Gimli', 'Erebor', '2022-02-07', 30),
   (2, 'Gandalf', 'Maia', '2022-03-10', 30),
   (3, 'Thorin', 'Erebor', '2022-03-16', 30),
   (5, 'Aragorn', 'Somwhere', '2022-01-11', 30),
   (6, 'Boromir', 'Erebor', '2022-03-03', 30);


   DROP TABLE IF EXISTS `learners`;
   CREATE TABLE IF NOT EXISTS `learners` (
   `id` int(11) NOT NULL AUTO_INCREMENT,
   `name` varchar(255) NOT NULL,
   `email` varchar(255) NOT NULL,
   `active` tinyint(1) NOT NULL,
   PRIMARY KEY (`id`)
   ) ENGINE=MyISAM AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4;


   INSERT INTO `learners` (`id`, `name`, `email`, `active`) VALUES
   (1, 'Aragorn', 'email.aragorn@hotmail.com', 120),
   (2, 'Smeagol', 'email.smeagol@hotmail.com', 100),
   (3, 'Galadriel', 'email.galadriel@hotmail.com', 50);
   COMMIT;

3. Try the following selects
    - Get all data from the groups<sup>\*</sup>
      SELECT * FROM `groups`;
   
    - Get the name and email of the first learner, and alias the name to learner_name<sup>\*</sup>
      SELECT name AS learner_name, email 
      FROM learners
      WHERE id = 1;

4. 💩 happens - a group needs to be postponed
    - Update the start date of the first_group (make it two months later)<sup>\*</sup>
      UPDATE groups
      SET start_date = '2021-11-22 00:00:00.000'
      WHERE ID = 1;   

      - Introduce a new field `status` which can contain a long text indicating the reason for postponing (bonus points if it's a creative one)
        PART 1 add new field
        ALTER TABLE groups
        ADD status varchar(255)
        PART 2 add long text
        UPDATE groups
        SET status = 'If you dont do this exercise correctly then chaos monkey will be doing his friendly thingy'
        WHERE ID = 1;


5. One of the learners changed his/her mind and decided to be an astronaut
    - Delete someone from the learners table<sup>\*</sup>

### 🌼 Nice to have (doable)

6. A learner belongs to a group, and a group has a coach
    - Find a technique to make this connection in the database (what of the field is unique to a record, so we can refer to it?)
7. We want all the data
    - Select a coach and all related groups<sup>\*</sup>
    - Select all the above, but also all learners from this group who are still active<sup>\*</sup>

### 🌳 Nice to have (hard)

Bonus round: try some steps again, but this time run your SQL from PHP.
You'll need to connect PHP to the database first. What techniques can you find to do so? Why do you choose one or another? Don't overthink the structure at this point, one file is enough.

Enjoy the ride! Don't forget to look back at what you've achieved so far every once in a while - you'll be old before you know 🙃
![](https://media.giphy.com/media/2nJgpMuR2fVn2/giphy.gif)