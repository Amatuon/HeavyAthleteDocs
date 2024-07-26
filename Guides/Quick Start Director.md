# Welcome to Heavy Athlete

This guide is designed to get your director profile in tip top shape and to get you hosting a game as fast as possible.

First things first your director account is an extension of your athlete account so make sure that you are good there. For help follow our [[Quick Start Athlete]] guide.

If you haven't already made an account with us [Sign Up](https://heavyathlete.com/auth/register/) and [Login](https://heavyathlete.com/auth/login/) the rest of this guide assumes you are logged in. 

To become a game director with Heavy Athlete navigate to your [[Athlete Page]]. Since you are logged in you can find this by clicking your name in the [[Navbar]]. At the bottom of the page is the [[Update Profile]] link. Click it.

On this page you should see a link that says "Become a Game Director" click it.

This is the page where the magic happens. 
- First thing you'll see at the top is onboarding instructions read them. I'm not going to repeat myself here. 
- Second you will see our terms of service and privacy policy your continued use of the site implies consent with them. If you don't like them I'm not forcing you to be here. 
- Third is pricing this one is really important. The text is pretty dense but I think the table explains it well. Basically unless we have to collect more than 5% to pay [[Stripe]] (our payment processor) then we don't. The total app fee (again unless required to pay Stripe) is 5%. We hand Stipe their fee out of the 5% and we keep the left over of that 5%. You keep all the rest. When you enter a price in the [[Game Dashboard]] you will also be notified of all the fees. We believe in total transparency and want to keep you informed.
- Below that you have some info boxes which will become your [[Director Page]].
	* First is your director email. This can be different to your athlete email (the one you used to sign up for Heavy Athlete). This email will receive notifications when athletes join games and be the primary one used to communicate with athletes as a director.
	* Second is your director name. This can be anything but I suggest you use something meaningful. A game put on by Witz Warriors sounds a lot more impressive than a game put on by Gerald Witzman. 
	* Third is your affiliation. This feature is unimplemented and can be safely ignored for now.
	* Fourth is your director bio. This is so that you can say a little something about your self. This box is [Markdown](https://www.markdownguide.org/basic-syntax/) compatible so feel free to insert links to socials, your own website, logos you know branding stuff. You have the same warning as the [[Athlete Page]] I don't care what you put here but so help me if you put child porn on my site I'm handing you over to the cops. Just stay legal here I don't even care if you stay classy.
	* Finally you have a selector for the emails to receive. The default is all of them. Many people complain that there are too many so I would recommend switching to "Athlete Joins a Game" or "No Emails about Athletes please"
	You will see this same information anytime you update your director profile.
- Finally you have a button which will send you to our payment processor [[Stripe]]. Stripe is a reputable company that securely handles online payments. When Heavy Athlete was created they offered the lowest rates for their service and had a great programmer interface for me to connect to. 
	Side notes: on Stripe: 
	* The reason that you have to enter a lot of data on Stripe is that its sensitive but your making money so the government needs to know. The important take away to that is you enter that sensitive info to Stripe not Heavy Athlete. I do not and cannot know any sensitive data about you. That adds some headache during coding but the upside is that even if Heavy Athlete is hacked, taken down, etc... your money and sensitive info isn't here so it can't be stolen via us. 
	* Please make sure that you complete your onboarding with Stripe or you will not be able to receive payments through Heavy Athlete.
	* You can connect an already existing Stripe account if you prefer.
	* After you have set up your Stripe Account you will have a fully capable Stipe Account this means that you can run payments or set up a store on Stripe if you would like. All that Heavy Athlete is allowed to do to your account is sell on your behalf. 
	* You get all the money directly from the customer then automatically send the transaction fee to Heavy Athlete. The money is never in our hands before yours.

Okay hopefully your back from Stripe. I know that was a lot of questions but with your account linked you are ready to make a game. 

You should notice that in you navbar you have a new link called [[Director Dashboard|AD Dashboard]]. This has quick access to everything you need. Since you have no games yet the Modify a game section should be empty. As you add games this will start to fill with links to those game's [[Game Dashboard]]. Eventually you will have too many games and this will switch to a search bar with the same function. Next you have a big button that says [[Create a Game]]. That's what you want to click. Modify profile will let you tweak your [[Director Page]] and go to Stripe goes to Stripe. 

Alright so you've clicked on [[Create a Game]]. This page will let you enter required info about the game. Most things should be self evident but here is the cliff notes:
- Solo or Team allows you to change how sign ups work for athletes for more info read [[Solo or Team]].
- The Athlete Cap is currently not truly hard and fast in team and mixed mode read about it on our [Discord](https://discord.com/channels/1196144078795067512/1202224076408762448.) You may need to join first [Join our Discord](https://discord.gg/76C2WeTV9B)
- Does the athlete get a free T-Shirt modifies the athlete sign up prompt to collect the athlete's preferred size. This data is then available to you in the [[Game Dashboard]].
- The description is [Markdown](https://www.markdownguide.org/basic-syntax/) compatible read what this means above.
- City and State are not required for us but if you want athletes to be able to refine their search to games near them you should include them. 
- State should also be a 2 letter code if you intend to upload you game results to [NASGA](http://nasgaweb.com/dbase/main.asp). Don't worry this is a one click feature on Heavy Athlete
- Athletes won't be able to sign up for your game until the open registration date and will no longer be able to sign up for your game after the close registration date or the last day of competition whichever comes first.
- Finally pick your available classes. Those button are drop downs. By default no classes are selected. If you don't open any up no one will be able to join. Athletes can only select classes that they are eligible for eg. I as a young man cannot enter as a Master or as a Woman

When you are done hit the Create Game Button. You should be sent to the [[Game Page]] for the game you just created. 

You could be done now but there are a few more things to know about. Below your description and above the athletes table you should see a link called "View Dashboard" click it.

You should now be on your game's [[Game Dashboard]] you will have a different one of these to control each game. I'm gunna run down the links on the side in order
- The main page shows all athletes signed up for the game. They split into groups according to their payment status and waiver status.
- The [[Communicate Feature|Communicate]] tab lets you send emails to athletes registered for this game. If you don't specify any filters then it gets sent to all athletes. If you click BCC you will have a list of all athletes, Clicking an athlete here overwrites all other settings and ensures only the selected athletes receive the message. If BCC is left blank then [[Flights]] and [[Classes]] can be clicked to filter to only send to athletes that belong in that group. If you select a lot from both categories you should know that the email is sent to the intersection of the union of all selected Flights and the union of all selected Classes (if that set theory left you in the dust maybe don't use the classes and flights features together). Finally Reply to is the email address that should receive replies from athletes. This defaults to your director email if left blank. Or you can enter any you want. If you don't want athletes to be able to reply to you set it to theheavyathlete@gmail.com trust me we don't care enough to reply on your behalf. For more info read [[Communicate Feature]].
- The [[Waivers]] tab lets you upload waivers for athletes to sign. Waivers are [Markdown](https://www.markdownguide.org/basic-syntax/) compatible and represent a legal contract between you and your athletes. I am not a lawyer and nothing I say is legal advice. That be said I recommend uploading a waiver for athletes to sign. If you have a waiver attached to the game athletes cannot sign up unless they sign the waiver. Heavy Athlete has the ability to collect legally valid electronic signatures from athletes. You will be able to see all signed waivers on the site. Heavy Athlete does not provide any waiver text for you to use even sample text because waiver laws differ from state to state and country to country and again I am not a lawyer this is not legal advice. If you do not feel comfortable using a waiver service created by a man you just told you twice he is not a lawyer I understand completely. I would still recommend making athletes sign a paper waiver on game day to protect yourself. One last time to be crystal clear I am not a lawyer and nothing I say is legal advice.
- Update Game Profile takes you back to a familiar screen. You already had to enter all this to make the game but now you can tweak it if needed.
- Update Scores takes you to a page with every athlete broken up by flight. When you are done entering scores hit submit at the bottom.
- Update [[Flights]] allows you to create new flights and change the flight an athlete is in. You can use this to change teams, recognize judges and volunteers or just ignore it. To learn more read [[Flights]] and [[Flights vs Classes]]
- Update [[Classes]] allows you to move athletes between classes they are eligible for. You will need this if an athlete doesn't weight in as a lightweight game day. We recommend using the class of other for non throwing Judges and Volunteers to not confuse [[Rankings]]. To learn more read [[Classes]] and [[Flights vs Classes]]
- Add Athlete allows you to add an athlete to the game. First Search for the athlete and select their name from the list. If you cannot find the athlete you are looking for click the "Add New Athlete" button this will create a new athlete in the Heavy Athlete database that can be claimed later. When you are happy that the athlete you wish to add is in the Name box hit "Submit". Athletes added this way are always added with the class of other and should be switched to a better class using Update Classes
- View Game Shop Orders is Not Implemented and can be safely ignored for now
- Modify Free Shirt Options allows you to pick the sizes available for athletes to select. By default XS - 4XL are selected.
- Go to Stripe is a link which send you to Stripe
- Send to NASGA will upload the game to the historical [NASGA](http://http://www.nasgaweb.com/dbase/main.asp) database. This will not overwrite data on NASGA so only click it when you are satisfied with your data entry under Update Scores

And that's it. There is still a tremendous amount that you can do on the site and a lot of documentation that covers it. Feel free to explore at your own pace and if you ever need help the best option is to [Join our Discord](https://discord.gg/76C2WeTV9B) and ask there.