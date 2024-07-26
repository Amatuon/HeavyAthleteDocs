# Database Nonsense

Warning this is really nerdy. You probably don't need to read this page unless you are trying to contribute to, steal from, or maintain the site.

Below is a copy of the database schema comments added for support

```sql
CREATE TABLE nasga_athlete ( -- user_id connects this to our athletes. If a user_id field exists use its data instead. This record type is really just a name with first and last added for convience. first and last name are generated on the fly if they don't already exist

    id INTEGER NOT NULL PRIMARY KEY,

    name TEXT NOT NULL, 
    
    user_id INTEGER, 
    
    first_name TEXT, 
    
    last_name TEXT,

);

CREATE TABLE nasga_score ( -- these represent scores imported from nasga they can only be modified by the system via an update or an admin. Note to admins don't update them raw as the next system update will revert your work

    id INTEGER NOT NULL PRIMARY KEY,

    nasga_athlete_id INTEGER NOT NULL, -- who does this belong to

    game_id INTEGER NOT NULL, -- which game does this belong to

    pro BOOLEAN NOT NULL, -- this isn't really used anymore. We were planning a more official pro system and decided that it was to messy. We wouldn't have been able to please everyone so we decided in the name of neutrallity to just make pro a class not a major disctinction

    flight TEXT NOT NULL, -- this is misnamed and should be changed but I don't want to track it down everywhere. NASGA doesn't have a concept of flights it kinda does hence the name but this would be more consistant with the name class

    date DATE NOT NULL, 

    sheaf TEXT, 

    wob TEXT,

    heavy_hammer TEXT,

    light_hammer TEXT,

    braemar_stone TEXT,

    open_stone TEXT,

    heavy_weight TEXT,

    light_weight TEXT,

    caber TEXT,

    FOREIGN KEY(nasga_athlete_id) REFERENCES nasga_athlete (id),

    FOREIGN KEY(game_id) REFERENCES game (id)

);

CREATE TABLE IF NOT EXISTS "user" ( -- this was originally going to be athlete and directors would have been separate. Couldn't figure out how to make that work with flask-login so they got merged

    id INTEGER NOT NULL,

    type VARCHAR NOT NULL, -- everyone has athlete which as I write it I realize that I can remove that data then, we append 'director' to it when you become a director and 'admin' if you become an admin. An inclusion test on this filed can tell you what type of account you are dealing with

    email VARCHAR NOT NULL,

    password VARCHAR NOT NULL, -- these are encrypted

    name TEXT NOT NULL, 
    
    "address_id" INTEGER, -- points to the address table but is unused

    phone_number TEXT, -- unused much like address this would have been helpful but we took the site in a different direction

    bio TEXT, -- Markdown compatable

    first_name TEXT NOT NULL, -- generated off of name. Turned out to be better to store them separate instead of solving on the fly to display names in Last, First order on the search bar

    last_name TEXT NOT NULL,

    gender TEXT NOT NULL, -- this is litterally 'M' or not 'M' honestly could have gone with a boolean but then I would never remember which way I set it up. I don't care how people choose to express themselves but the sport only has one gender distinction Men's vs. Women's classes

    date_of_birth DATE NOT NULL, -- used to calculate age so that masters scores are always in the correct class

    pro_id INTEGER, -- unused. We moved a away from a formal pro system

    liability_release INTEGER, -- unused. Virginia law has a section for implied consent to TOS 

    t_shirt_size TEXT, -- unused. Needs implementation. Would simply remember an athletes size and select it by default when they sign up for a game

    director_id INTEGER, 
    
    "director_stripe_id" TEXT, -- this is a unique identifier given out by stripe. We can use it to send payments to the director without knowing any of their banking details
    
    "director_address_id" INTEGER, -- unused. see all the other address comments

    director_name TEXT, -- Doesn't just have to be the same name as the athlete. You could put 'Going Rogue' or 'The Barn Gym' do people no but they could

    director_email TEXT, -- Doesn't have to be the same as user email

    director_bio TEXT, -- Markdown compatable

    affiliation TEXT, -- unused. Effectively became the group system.
    
    "no_app_fee" INTEGER NOT NULL DEFAULT 0, -- this is a super secret boolean. False / 0 and you are normal and I get a cut of your game signups. True / 1 and you still have to pay Stripes fees but I collect nothing. There are not many people on this list but I am open to extending no app fee to charitable organizations
    
    director_email_preferences INTEGER NOT NULL DEFAULT 0, -- see the actual code for what the numbers mean
    
    `city` TEXT, -- used with the other geo data to prefill the game radial search 
    
    `state` TEXT, 
    
    `country` TEXT, -- in addition to the game radial search you also get your flag by your name. Thanks to Tedd Van Vleck from SMAI for that awesome idea.
    
    `freedom_units` INTEGER DEFAULT 1, -- boolean if false we convert everything to SI units for you
    
    `color_records` INTEGER NOT NULL DEFAULT 2, -- 0 is off, 1 and 2 distguish between SB and PRs but I don't remember which is which

    PRIMARY KEY (id),

    UNIQUE (email)

);

CREATE TABLE claimable_score ( -- Claimable scores originate from our system for athletes that haven't signed up yet. Thus they are claimable like a nasga_score but also more complete like our own scores

    id INTEGER NOT NULL,

    athlete_id INTEGER, -- who has is been claimed by, technically we can get this from querying on nasga_athlete_id and checking there but this is way more convienent

    nasga_athlete_id INTEGER NOT NULL,

    game_id INTEGER NOT NULL,

    pro BOOLEAN NOT NULL, -- unused. Just like nasga_score

    date DATE NOT NULL,

    historic BOOLEAN NOT NULL, -- weather or not we have attached a nasga_score to it helps avoid duplicates in system

    athlete_lightweight BOOLEAN NOT NULL, -- this idea kind of got overwritten by classes

    nasga_class TEXT NOT NULL,

    flight TEXT,

    field_id INTEGER, -- unused. would be used for determining field records

    payment_status TEXT,

    place TEXT,

    games_points TEXT,

    sheaf TEXT,

    wob TEXT,

    heavy_hammer TEXT,

    light_hammer TEXT,

    braemar_stone TEXT,

    open_stone TEXT,

    heavy_weight TEXT,

    light_weight TEXT,

    caber TEXT, 
    
    `list_of_custom_events` TEXT, -- all custom events get crammed in here as json

    PRIMARY KEY (id),

    FOREIGN KEY(athlete_id) REFERENCES user (id),

    FOREIGN KEY(nasga_athlete_id) REFERENCES nasga_athlete (id),

    FOREIGN KEY(game_id) REFERENCES game (id),

    FOREIGN KEY(field_id) REFERENCES field (id)

);

CREATE TABLE IF NOT EXISTS "score" (

    id INTEGER NOT NULL,

    athlete_id INTEGER NOT NULL,

    game_id INTEGER NOT NULL,

    pro BOOLEAN NOT NULL, -- unused. The pro system was abandoned as it was too hard to implement

    date DATE NOT NULL,

    historic BOOLEAN NOT NULL, -- do we have a score to shadow with this one
    
    "athlete_lightweight" BOOLEAN NOT NULL DEFAULT 0, -- this idead kinda got overwritten by classes
    
    "nasga_class" TEXT NOT NULL, 
    
    "flight" TEXT,

    field_id INTEGER, "payment_status" TEXT, waiver_status TEXT, "place" TEXT, "games_points" TEXT,

    sheaf TEXT,

    wob TEXT,

    heavy_hammer TEXT,

    light_hammer TEXT,

    braemar_stone TEXT,

    open_stone TEXT,

    heavy_weight TEXT,

    light_weight TEXT,

    caber TEXT, shirt_order_id INTEGER REFERENCES "game_shop_order"("id"), checkout_session_id TEXT, `list_of_custom_events` TEXT,

    PRIMARY KEY (id),

    FOREIGN KEY(athlete_id) REFERENCES user (id),

    FOREIGN KEY(game_id) REFERENCES game (id),

    FOREIGN KEY(field_id) REFERENCES field (id)

);

CREATE TABLE donation (

    id INTEGER NOT NULL,

    name TEXT NOT NULL,

    amount INTEGER NOT NULL, -- in pennies like all prices on Stripe

    date DATE NOT NULL,

    PRIMARY KEY (id)

);

CREATE TABLE game_shop_product ( -- Currently only free shirts although we do plan to expand

    id INTEGER NOT NULL,

    creator_id INTEGER NOT NULL,

    game_id INTEGER NOT NULL,

    name TEXT NOT NULL,

    price INTEGER,

    description TEXT NOT NULL,

    options TEXT,

    notes TEXT,

    PRIMARY KEY (id),

    FOREIGN KEY(creator_id) REFERENCES user (id),

    FOREIGN KEY(game_id) REFERENCES game (id)

);

CREATE TABLE game_shop_order (

    id INTEGER NOT NULL,

    game_id INTEGER NOT NULL,

    user_id INTEGER NOT NULL,

    lines TEXT NOT NULL, -- json

    status TEXT NOT NULL,

    PRIMARY KEY (id),

    FOREIGN KEY(game_id) REFERENCES game (id),

    FOREIGN KEY(user_id) REFERENCES user (id)

);

CREATE TABLE IF NOT EXISTS "game" (

    id INTEGER NOT NULL,

    name TEXT NOT NULL,

    director_id INTEGER NOT NULL,

    start_date DATE NOT NULL,

    end_date DATE NOT NULL,

    historic_id INTEGER, -- used to shadow the imported game

    field_id INTEGER, -- unused. would be helpfull if we implement fields
    
    "waivers" TEXT, -- json holding a list of all MD files that served as waivers. This is an append only list
    
    registration_open DATE,

    registration_deadline DATE,

    description TEXT, -- Markdown compatable
    
    "available_classes" TEXT, 
    
    custom_flights TEXT, 
    
    city TEXT, -- geo data is for NASGA and for radial game finder
    
    state TEXT, 
    
    country TEXT, 
    
    "team_configuration" TEXT DEFAULT 'solo', 
    
    "athletes_per_team" INTEGER DEFAULT 2, 
    
    "unclaimed_team_tokens" TEXT, 
    
    "claimed_team_tokens" TEXT, 
    
    "athlete_cap" INTEGER DEFAULT -1, 
    
    athlete_free_shirt INTEGER DEFAULT 0, 
    
    "shop_listings" TEXT, -- json
    
    game_shirt_id INTEGER REFERENCES "game_shop_product"("id"), 
    
    `price` TEXT, 
    
    `team_price` TEXT, 
    
    logo_url TEXT, 
    
    `secure_signup_token` TEXT, 
    
    `secure_signup_tokens` TEXT,

    PRIMARY KEY (id),

    FOREIGN KEY(director_id) REFERENCES user (director_id),

    FOREIGN KEY(field_id) REFERENCES field (id)

);

CREATE TABLE field ( -- this is unused. Eventually we would like to support field records and this would be used then

    id INTEGER NOT NULL,

    name TEXT NOT NULL,

    address TEXT,

    PRIMARY KEY (id)

);

CREATE TABLE address ( -- this is unused. Turns out city, state, country was good enough. In a previous hypothetical version of the site we would have needed to mail checks like iron podium so I was prepared

    id INTEGER NOT NULL PRIMARY KEY,

    city String,

    country String,

    line1 String,

    line2 String,

    postal_code String,

    state Sting

);


CREATE INDEX idx_user_id ON nasga_athlete (user_id);
```

You may have noticed that we have 3 types of scores. They could all be folded into claimable_scores but the the distinctions are helpful. Scores are made by us and changeable by us, we don't care what happens on NASGA we are the source of truth. Nasga_scores are imported so they are what they are. They get overwritten by the system periodically.  Claimable scores for people that haven't joined the site yet. They function like normal scores in all ways except they can be claimed later.1222