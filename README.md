import inventoryClass

class Engine(object):
	
	def __init__(self, scene_map):
		self.scene_map = scene_map
		
	def play(self):
		current_scene = self.scene_map.opening_scene()
		last_scene = self.scene_map.next_scene('escape_van')
		
		while current_scene != last_scene:
			print '-' * 30
			next_scene_name = current_scene.enter()
			current_scene = self.scene_map.next_scene(next_scene_name)
			
		current_scene.enter()
		
		
class Scene(object):
	
	def enter(self):
		print "This scene is not yet configured. Subclass it and implement enter()"
		exit()

class Introduction(Scene):
	
	def enter(self):
		inv.reset_items()
		print "The year is 2021. Autonomous driving vehicles are commonplace vehicles. Tesla owns NASA, "
		print "but they still have not released the Model 3. You find yourself in the back of a Tesla Model-"
		print "X sitting besides someone who has long lost her glory. Robbing the Global Bank is your only "
		print "shot at getting some money so you can start trading stocks again. This is your only hope in "
		print "life. Pretty sad, but it's the reality."
		print
		print "H. Clinton: Alright hot stuff, this is what we've been waiting for. It's time to gear up."
		print 
		print "By the way.. I never got your name."
		print
		name = raw_input("What is your name? ")
		print '-' * 30
		print "Clinton: Ah, your mama named you that? I'm just having a little fun. Get ready %s." % name
		print
		print "Clinton: I got a nice selection of tricky yet effective options to choose from. Don't "
		print "you dare question the effectiveness of the weapons I am about to show you. If you do, "
		print "I swear I will blow your god damn face off. That's what I did to Bill after Lewin.. Nvm."
		print
		print '-' * 30
		go = raw_input("Ready whenever you are, just say 'ready' > ")
		if go == 'ready' or 'rdy' in go:
			return 'start_room'
		else:
			print "Although your input wasn't a valid response, we'll still move forward."
			return 'start_room'
		
class StartRoom(Scene):
	
	def enter(self):
		print "Alright, pick your poison. Just give me a number."
		print "1. Putty Knife"
		print "2. Handgun with no Ammo"
		print "3. Shotgun with No Shells" 
		print "4. Ask, 'Do you have anything more useful?'"
		print '-' * 30
		choice = raw_input("> ")
		
		if choice == '1':
			inv.add_item('Putty Knife')
			print "A", 
			inv.print_items(),
			print "was added to your inventory."
			print "Clinton: Nice selection. We're about to arrive at our destination."
			return 'entrance'
	
		elif choice == '2':
			inv.add_item('Handgun')
			print "A", 
			inv.print_items()
			print "was added to your inventory."
			print "Clinton: Nice selection. We're about to arrive at our destination."
			return 'entrance'
	
		elif choice == '3':
			inv.add_item('Shotgun')
			print "A", 
			inv.print_items()
			print "was added to your inventory."
			print "Clinton: Nice selection. We're about to arrive at our destination."
			return 'entrance'
			
		elif choice == '4':
			print "The ex-presidential candidate stares at you for a moment. Her pupils dilate and "
			print "her eyes grow black like oil."
			print
			print "Clinton: Monica Ruined-skied my chance at becoming the president and I vowed to never"
			print "let myself be questioned again. Get out of my car!!"
			print
			print "Clinton pushes you out of the car and drives away. You realize you are left with"
			print "nothing. You had no life, no friends, and now, no Clinton."
			print 
			print "*bzzzzzzzzz* A killer bee flies past you. You're allergic to bees. Killer ones especially."
			print "*poke* A homeless man stabs you from behind, harasses you briefly, and then skips away."
			print "You bleed out from the right ass cheek and look up at the sky as your vision goes dark."
			print "You contracted a new kind of STD that kills homosexuals within a matter of seconds."
			return 'death'
			
			
		else:
			print "Clinton: I don't have that. Stop wasting my time. Time is money. I spent all"
			print "my money in the 2016 election. You already know what happened."
			return 'start_room'
			
		

			
class Entrance(Scene):
	
	def enter(self):
		print "*SKKKRRRR* The car makes a screeching halt in front of a building that stretches "
		print "up higher than the clouds. You put on your 'Anonymous' mask and step out of the vehicle."
		inv.remove_item('Unmasked')
		print "You look up at the facade and see intricate placement of diamonds that spells, 'The Global Bank'."
		print 
		print "You see guards ordering food at a nearby bacon-wrapped hotdog stand down the street."
		print "It's probably best to avoid them."
		print
		print 'What would you like to do?'
		print '1. Walk into the Bank.'
		print '2. Take a selfie.'
		print '3. Walk over to the delicious smelling hotdog stand and ask if you can order two bacon-wrapped hotdogs'
		print "4. Flick Hillary the middle finger and yell, 'Guards! Clinton is trying to coerce me to do bad things!'"
		print '-' * 30
		choice = raw_input("> ")
		
		if choice == '1' or 'walk' in choice:
			print "You walk briskly up the steps and pull the thick golden hand bar attached to one of the "
			print "gigantic double doors and feel a chilly air-conditioned breeze wift through the opening"
			print "and cool your warm face through the mask's eyeholes as you enter the Bank."
			return 'teller'
		
		if choice == '2' or 'selfie' in choice:
			print "You pull out your iPhone 9S Plus Infinity and press the SnapChet icon. Small lenses "
			print "project a holographic display that shows you some videos that were posted by celebrities."
			print "You take a selfie with your Anonymous mask on and the Global Bank logo in the background."
			print "You feel someone grab your shoulder so you turn around. It's one of the Bank guards."
			print
			print "Geraldo: 'You do know that this mask is illegal since Anonymous leaked nude photos of "
			print "Donald Trump? You're coming with us.'"
			print 
			print "Electric cuffs are placed around your neck. You're going to jail. You feel overcome with regret..."
			return 'death'
			
		if choice == '3' or 'hotdog' in choice:
			print "You walk over to the hotdog stand and decide to hide your mask while walking over. The guards"
			print "are arguing with the Mexican tender about something."
			print
			print "*Ahem*.. 'Excuse me? Senor?' The guards and Mexican turn to look at you. Good thing you took "
			print "4 years of Spanish in highschool."
			print "'Quieremos quatro panchos con tocino y todos por fa. Quanto questan? Me puede dar un descuento?'"
			print
			print "The Mexican looks at you pleased. 'Si senor,' and begins grilling four bacon wrapped hotdogs and"
			print "onions with bellpeppers. He squirts ketchup, mayonnaise, and mustard on the hotdogs and hands them to you."
			print "You tell him, 'Solo tengo cinco dolares'."
			print "The Mexican smiles and nods and hands you the hotdogs and takes your money."
			print "The guards look at you as if you knew the language of some aliens."
			print 
			print "1. Walk away and take a bite of one of the delicious smelling hotdogs."
			print "2. Offer to give the three guards one hotdog each."
			print '-' * 30
			
			hotd = raw_input("> ")
			
			if hotd == '1' or 'walk' in hotd:
				print "You take a bite of the hotdog and choke on some dirt that was not propertly cleaned"
				print "from the bell peppers. You gasp for air and the guards take your wild movements as"
				print "a threat. They take out their steel clubs and start beating you. You suffocate on the"
				print "dirt and start to bleed from your skull. You die from one hard crack to the head."
				return 'death'
					
			if hotd == '2' or 'give' or 'offer' in hotd:
				print "You offer the guards each a hotdog. They seem enthralled."
				print
				print "Guard: 'I told Jimmy to bring some damn cash but he spent all his cash at the valet. Parking"
				print "costs are ridiculous these days. I appreciate your gesture, stranger. Here, take this. I"
				print "found this wallet while tending the grounds. There's no money in it, but it's a real nice wallet.'"
				inv.add_item('Wallet')
				print
				print "A Luxurious Leather Wallet was added to your inventory."
				print
				print "Stop wasting time. You should really head into the Bank now."
				print '-' * 30
				ans = raw_input ("Tell me when you are ready to proceed: ")
				if ans == 'ready' or 'rdy' or 'Ready' in ans:
					return 'teller'
				
			else:
				print "Not a valid choice. Try again."
				return 'entrance'
			
		elif choice == '4':
			print "*eee* You feel a tingle inside your neck. The guards turn to you from the hotdog cart and begin"
			print "to walk toward you. The tingle inside your neck is starting to feel like a needle through your brain."
			print "*sssss* You hear a high pitched noise from within making your vision fill with red. You begin "
			print "to bleed from your eyes and ears. The piercing sound stops and you can barely make out a voice. 'I "
			print "knew you were a rat, darling.'"
			print "*SWEEEEE* the noise is too much to bear. You drop to your knees and you begin to fall unconscious."
			print "The guards muffled scream 'CALL FOR MEDICAL DISPA...' is heard before your head explodes."
			return 'death'
			
		else:
			print "That is not a valid choice. Try again."
			return 'entrance'
				
class Teller(Scene):

	def enter(self):
		print "You enter the lobby and see white marble floors, brightly lit from the crystal"
		print "blue lights gleaming upon each structural slab pillar with gallant pictures of "
		print "global leaders upon the walls. You notice a portrait of Donald Trump on the wall."
		print
		print "To your left, you see a caged door that leads into the Security Room."
		print "To your right, you see some men in uniform transporting a pallet into a corridor,"
		print "and a silver tag on the pallet says, 'Vault'"
		print
		print "You walk up to the teller. The teller looks at you with kindness in her eyes."
		print "You notice that she has on a soft blue pendant on her pink blouse. Her nametag reads"
		print "'Alison White'"
		print
		print "Alison: 'Welcome to Global Bank. Thank you for choosing us for your banking needs."
		print "How... may I assist you today?'"
		print
		print '-' * 30
		print "1. 'Hello Alison, I'd like to make a withdrawal.'"
		print "2. 'This is a heist! Shut up and give me all your money or you die today.'"
		print "3. Attack her with your weapon."
		print "4. Compliment her and then ask her for her phone number."
		print '-' * 30
		print
		choice = raw_input("> ")
		
		if choice == '1':
			print "'Hello Alison, I'd like to make a withdrawal.'"
			print '-' * 30
			print "Alison's smile retreats slightly."
			print
			print "Alison: 'Sure, I can help you with that... Mind if I ask you what the scary mask"
			print "is all about? You do know that since the ever incident.. that mask is.. illegal?'"
			print '-' * 30
			print "1. 'I don't have time for this. Give me all the money in your register.'"
			print "2. 'My buddies dared me to walk in with this mask on. Please don't freak out.'"
			print "3. Remain silent."
			print "4. Attack her with your weapon."
			print '-' * 30
			ini = raw_input("> ")
			if ini == '1':
				inv.remove_item('Wallet')
				print "You begin to get impatient. You tell Alison, 'I don't have time for this."
				print "Put all the money you have in your register on the counter, and if you give"
				print "me even a sliver of the idea that you are trying to sabotage me, I won't let you live.'"
				print
				print "**You pull out your",
				inv.print_items()
				print
				print
				print "She stares at you with horror for a moment before her senses return."
				print 
				print "Alison: Ok, Ok ok.. Please, just don't hurt anyone here. This is all I have."
				print 
				print "Alison places $10,000 in cash in front of you and it appears that she's exhausted"
				print "her register. Customers are starting to look toward your direction. The tellers"
				print "start to notice as well. You begin to hear murmuring."
				print '-' * 30
				print "1. Take the cash and book it toward the exit."
				print "2. Ask her for the key to the Vault."
				print "3. Forget the cash and run toward the Security Room."
				print "4. Forget the cash and run toward the President's Office"
				print '-' * 30
				ini2 = raw_input("> ")
				if ini2 == '1':
					inv.add_item('5k')
					inv.remove_item('Wallet')
					print "You grab the cash and frantically run toward the exit."
					print "Sirens go off and the customers start to scream."
					print "You try to kick open the door but it's too heavy and so you recoil backwards."
					print '-' * 30
					print "You look around again scanning for any incoming guards. The Security office opens"
					print "and guards begin to pour out with their guns drawn."
					print "You press heavily against the door and the warm humid air outside feels sticky."
					print "You see the Tesla X parked outside. While running down the steps, you miss a step"
					print "and slip, but you catch yourself. You drop a few wads of $20 and $50 bills"
					print "while preventing your fall. Guards come running out of the door. Without even "
					print "attempting to pick up the money you dropped, you scurry into the SUV."
					return 'escape_van'
				if ini2 == '2':
					inv.remove_item('Wallet')
					print "You demand the key to the Vault with the assumption that there is more money"
					print "inside. Alison begins to explain that only the President has the key and starts"
					print "to cry. The tellers start backing away from your direction and customers begin"
					print "to pack up their belongings and walk quickly toward the exit. Time is running out."
					print 
					print "Alison: 'The Manager's desk is next to the Security Room. But I think he called"
					print "the day off sick. Please.. don't do this.' Tears streak down her face ruining her mascara."
					print "The Security office opens and guards begin to pour out with handguns drawn."
					print "Seeing as you don't really have much options.. you weigh your choices."
					print '-' * 30
					print "1. Take the cash and run."
					print "2. Threaten the guards with your",
					inv.print_items()
					print 
					print '-' * 30
					ini3 = raw_input("> ")
					if ini3 == '1':
						inv.add_item('10k')
						print "You grab the cash and run toward the exit. The guards begin to shoot and you"
						print "get shot on your right hand. With all your might, you press against the door and"
						print "blood gushes out of your hand as you push the door. You see the SUV waiting for you."
						print "you get in the van and the wheels burn out against the asphalt leaving a dark cloud"
						print "behind your escape."
						return 'escape_van'
					if ini3 == '2':
						inv.remove_item('Wallet')
						print "You point your",
						inv.print_items()
						print "at the guards"
						print
						print "They react by shooting back at you and a bullet hits you in eye. You shriek in pain"
						print "as you realize that you will either survive this and be forever crippled and a convicted"
						print "felon, or you will die in a feeble attempt to get back into trading stocks."
						print "With blood running down your face, you slump down on the cold marble floor."
						print "As your consciousness quickly fades, the last thing you catch a glimpse of are"
						print "Security Guards running through the front door with hotdogs in their hands."
						return 'death'
				if ini2 == '3':
					print "Without even collecting the money, you run toward the Security Room."
					return 'security_room'
				if ini2 == '4':
					print "Without even grabbing the money, you run toward the President's Office"
					return 'presidents_office'
			
			if ini == "2":
				print "You explain to Alison, 'Weird story, but my friend dared me to walk into this bank"
				print "with this mask on. Well, I lost a bet so I couldn't say no.'"
				print
				print "Alison stares at you blankly."
				print "Alison: 'So, you're just going to wear an illegal mask in a facility filled with "
				print "police officers and guards? You'd be arrested before you could even leave!"
				print
				print "You feel a sense of embarrassment rising up from your chest making your face feel hot."
				print '-' * 30
				print "1. Offer to take off your mask in exchange for her phone number."
				inv.remove_item('Wallet')
				print "2. Show her your",
				inv.print_items()
				print "and demand that she empty her register."
				print "3. Ask her about the President of the bank."
				print "4. Ask her about the lack of security at the Bank."
				print '-' * 30
				ini4 = raw_input("> ")
				if ini4 == '1':
					print "You try to pull off a friendly flirtatious offer to take the mask off in"
					print "exchange for her phone number. Alison is taken aback by the thought that this"
					print "entire fiasco was done just to get her number. You can see blood rushing into "
					print "her cheeks. She turns red."
					print
					print "Alison: 'My gosh. Although.. um.. I think that's very brave of you, but I can't "
					print "just give you my number. The mask you're wearing is illegal and I'm afraid of what"
					print "will happen next.'"
					print "The Security Office opens and two guards come walking your way."
					print 
					print "Alison: 'I'm so sorry... I had to report you. My career is on the line! Sorry..."
					print
					print "Guards ask you to remove the mask and come with them as you are under arrest."
					return 'death'
				if ini4 == '2':
					inv.remove_item('Wallet')
					print "You begin to get impatient. You tell Alison, 'I don't have time for this."
					print "Put all the money you have in your register on the counter, and if you give"
					print "me even a sliver of the idea that you are trying to sabotage me, I won't let you live.'"
					print
					print "**You pull out your",
					inv.print_items()
					print
					print
					print "She stares at you with horror for a moment before her senses return."
					print 
					print "Alison: Ok, Ok ok.. Please, just don't hurt anyone here. This is all I have."
					print 
					print "Alison places $10,000 in cash in front of you and it appears that she's exhausted"
					print "her register. Customers are starting to look toward your direction. The tellers"
					print "start to notice as well. You begin to hear murmuring."
					print '-' * 30
					print "1. Take the cash and book it toward the exit."
					print "2. Ask her for the key to the Vault."
					print "3. Run toward the Security Room."
					print "4. Run toward the President's Office"
					print '-' * 30
					ini2 = raw_input("> ")
					if ini2 == '1':
						inv.add_item('5k')
						print "You grab the cash and frantically run toward the exit."
						print "Sirens go off and the customers start to scream."
						print "You try to kick open the door but it's too heavy and so you recoil backwards."
						print '-' * 30
						print "You look around again scanning for any incoming guards. The Security office opens"
						print "and guards begin to pour out with their guns drawn."
						print "You press heavily against the door and the warm humid air outside feels sticky."
						print "You see the Tesla X parked outside. While running down the steps, you miss a step"
						print "and slip, but you catch yourself. You drop a few wads of $20 and $50 bills"
						print "while preventing your fall. Guards come running out of the door. Without even "
						print "attempting to pick up the money you dropped, you scurry into the SUV."
						return 'escape_van'
					if ini2 == '2':
						print "You demand the key to the Vault with the assumption that there is more money"
						print "inside. Alison begins to explain that only the President has the key and starts"
						print "to cry. The tellers start backing away from your direction and customers begin"
						print "to pack up their belongings and walk quickly toward the exit. Time is running out."
						print 
						print "Alison: 'The Manager's desk is next to the Security Room. But I think he called"
						print "the day off sick. Please.. don't do this.' Tears streak down her face ruining her mascara."
						print "The Security office opens and guards begin to pour out with handguns drawn."
						print "Seeing as you don't really have much options.. you weigh your choices."
						print '-' * 30
						print "1. Take the cash and run."
						print "2. Threaten the guards with your",
						inv.print_items()
						print 
						print '-' * 30
						ini3 = raw_input("> ")
						if ini3 == '1':
							inv.add_item('10k')
							print "You grab the cash and run toward the exit. The guards begin to shoot and you"
							print "get shot on your right hand. With all your might, you press against the door and"
							print "blood gushes out of your hand as you push the door. You see the SUV waiting for you."
							print "you get in the van and the wheels burn out against the asphalt leaving a dark cloud"
							print "behind your escape."
							return 'escape_van'
						if ini3 == '2':
							print "You point your",
							inv.print_items()
							print "at the guards"
							print
							print "They react by shooting back at you and a bullet hits you in eye. You shriek in pain"
							print "as you realize that you will either survive this and be forever crippled and a convicted"
							print "felon, or you will die in a feeble attempt to get back into trading stocks."
							print "With blood running down your face, you slump down on the cold marble floor."
							print "As your consciousness quickly fades, the last thing you catch a glimpse of are"
							print "Security Guards running through the front door with hotdogs in their hands."
							return 'death'
					if ini2 == '3':
						print "Without even collecting the money, you run toward the Security Room."
						return 'security_room'
					if ini2 == '4':
						print "Without even grabbing the money, you run toward the President's Office"
						return 'presidents_office'
				if ini4 == '3':
					print "You casually ask about how much the President of the bank much make on an annual basis."
					print "'So, the president must make enough income to afford beautiful things like your pendant!"
					print "Alison blushes at you."
					print "Alison: 'I am not dating the President. He's married. I think he is sick though. I didn't"
					print "see him here today. Take off your mask before the guards come and see you."
					inv.add_item('Unmasked')
					print "You take off your mask and put it away in your jacket."
					print
					print "'I'm sorry Alison, but I have to use the restroom. Mind if I come back to you?'"
					print "Alison nods and waves her hand signaling for the next customer."
					print '-' * 30
					print "1. Walk over to the President's Office."
					print "2. Ask Alison about the lack of security at the Bank."
					print '-' * 30
					ini5 = raw_input("> ")
					if ini5 == '1':
						print "You walk over to the President's Office."
						return 'presidents_office'
					if ini5 == '2':
						print "You ask Alison, 'So, what's the deal with the lack of security at this bank?"
						print "Isn't this bank known to carry most of the wealth of the nation?"
						print
						print "Alison looks at you strangely."
						print "Alison: Well, yes, but the security guards are usually in their rooms trying to"
						print "guess what the President's wife looks like. Apparently she married Donald Trump"
						print "and took half his wealth, reinvested it in the stock market, and is now one of "
						print "the world's richest women that has rarely been seen on media since Trump made it"
						print "against the law to take photos of her since he became president."
						print 
						print '-' * 30
						print "1. Walk over to the President's Office."
						print "2. Walk over to the Security Office."
						ini6 = raw_input("> ")
						if ini6 == '1':
							print "You walk over to the President's Office."
							return 'presidents_office'
						if ini6 == '2':
							print "You walk over to the Security Room"
							return 'security_room'
				if ini4 == '4':
					print "You ask Alison, 'So, what's the deal with the lack of security at this bank?"
					print "Isn't this bank known to carry most of the wealth of the nation?"
					print
					print "Alison looks at you strangely."
					print "Take off your mask before the guards come and see you."
					inv.add_item('Unmasked')
					print "You take off your mask and put it away in your jacket."
					print "Alison: Well, yes, but the security guards are usually in their rooms trying to"
					print "guess what the President's wife looks like. Apparently she married Donald Trump"
					print "and took half his wealth, reinvested it in the stock market, and is now one of "
					print "the world's richest women that has rarely been seen on media since Trump made it"
					print "against the law to take photos of her since he became president."
					print 
					print '-' * 30
					print "1. Ask her about the President of the bank."
					print "2. Walk over to the Security Office."
					ini7 = raw_input("> ")
					if ini7 == '1':
						print "You casually ask about how much the President of the bank much make on an annual basis."
						print "'So, the president must make enough income to afford beautiful things like your pendant!"
						print "Alison blushes at you."
						print "Alison: 'I am not dating the President. He's married. I think he is sick though. I didn't"
						print "see him here today. Take off your mask before the guards come and see you."
						inv.add_item('Unmasked')
						print "You take off your mask and put it away in your jacket."
						print
						print "'I'm sorry Alison, but I have to use the restroom. Mind if I come back to you?'"
						print "Alison nods and waves her hand signaling for the next customer."
						print '-' * 30
						print "1. Walk over to the President's Office."
						print "2. Walk over to the Security Office."
						ini6 = raw_input("> ")
						if ini6 == '1':
							print "You walk over to the President's Office."
							return 'presidents_office'
						if ini6 == '2':
							print "You walk over to the Security Room"
							return 'security_room'
					if ini7 == '2':
						print "You walk over to the President's Office."
						return 'presidents_office'
			
			if ini == '3':
				print "You stand there silently as Alison appears to get increasing uncomfortable."
				print
				print "Alison: Ok fine. Just don't say anything, will you? I'm going to call security."
				print
				print "You see her reaching toward a switch underneathe the desk."
				print "Time slows down."
				print
				print "1. While remaining silent, slowly reveal your",
				inv.print_items()
				print
				print "2. Give in to the pressure and respond, 'Ok you got me. Don't report me.'"
				print "3. Reach in through the teller window and grab Alison's hand."
				ini8 = raw_input("> ")
				if ini8 == '1':
					print "Reaching into your jacket, you pull out your", 
					inv.print_items(),
					print "and slowly raise it above the counter."
					print "Alison's eyes widen in surprise."
					print 
					print "Alison: 'Why would anyone bring a",
					inv.print_items(),
					print "into a bank? You're fierce. First I thought your mask was a bit much."
					print "But now I just want to hear all about you. Ask me out. Now. Tonight."
					print "I get off in half an hour.'"
					print "Alison smiles at you."
					print
					print "1. Take off your mask. You don't need money, you just need love."
					print "2. "
					ini9 = raw_input("> ")
					if ini9 == '1':
						inv.add_item('Unmasked')
						print "You laugh as you see a glimmer in Alison's eyes. Are you in love? Are you willing to"
						print "give up your plans to rob the world's largest bank for true love?"
						print "You take off your mask and you notice that three guards walking toward your direction."
						print "Alison hands you a folded piece of paper."
						print '-' * 30
						print "1. Read the piece of paper."
						print "2. Ignore the note and walk toward the Security Room."
						print "3. Thank Alison and walk toward the exit."
						print
						print '-' * 30
						ini10 = raw_input("> ")
						if ini10 == '1':
							print "You open up the folded note and it reads 'Sike! I don't affiliate"
							print "with criminals. That mask is illegal since the group 'Anonymous' leaked"
							print "nude photos of Donald Trump on the internet. Do you live under a rock?"
							print "You feel something grab you by your wrist."
							print "'You're under arrest, scum.'"
							return 'death'
						if ini10 == '2':
							print "Acknowledging the presence of danger, you realize that you should get moving."
							print "You leave the teller, circle around a line of customers, and then"
							print "You make a break toward the Security Room."
							return 'security_room'
						if ini10 == '3':
							print "You wink at Alison and turn around toward the exit. The guards start "
							print "to pick up their pace to a slight jog. You run toward the exit and leave"
							print "the bank and you see the SUV parked waiting for you. You get in the van and leave."
							print 
							print "While in the van, You open the folded note and it reads:"
							print "'Sike! I don't affiliate with criminals. That mask is illegal since the group"
							print "'Anonymous' leaked nude photos of Donald Trump on the internet. Do you live under"
							print "a rock?' You feel a wave of embarassment and the feeling of regret fills your chest."
							return 'escape_van'
					
				if ini8 == '2':
					print "You blurt, 'OK, calm down. I'm just playing around. Can't a guy joke with'"
					print "a pretty girl?'"
				if ini8 == '3':
					print "You reach in and grab her hand. You feel your",
					inv.print_items()
					print "slip out of your pocket."
		
		if choice == '2':
			inv.remove_item('Wallet')
			print "Time is of the essence. The time to act is now."
			print "You tell Alison, 'This is a fuckin' heist. Give me all the money in the register.'"
			print 
			print "For a brief moment, Alison looks at you confused. Her senses return and she calmly looks"
			print "to her right and left, then looks back to you."
			print "Alison: 'Are you sure you want to do this?'"
			print 
			print "1. Reveal your",
			inv.print_items()
			print "and point it toward Alison."
			print "2. 'Ok, you got me. I'm just kidding!'"
			ini11 = raw_input("> ")
			if ini11 == '1':
				print "You point your",
				inv.print_items()
				print "at Alison. She gasps loudly."
				print "Everyone in the room looks toward your direction. Shit. The Security Room door opens"
				print "and three guards come running out with guns drawn."
				print 
				print "You reach into the window and grab Alison's arm and press your weapon on her forehead."
				print "'I WILL KILL HER IF ANYONE COMES ANY CLOSER."
				print "The Guards stop in their tracks."
				print 
				print "Guard: Calm down. What do you want?"
				print 
				print '-' * 30
				print "1. Tell the guards to drop their handguns and move to the side of the lobby."
				print "2. Demand the guards to go into the Vault and empty out all the inventory in a bag."
				ini12 = raw_input("> ")
				print '-' * 30
				if ini12 == '1':
					print "You yell, 'Drop the fuckin' weapons and move to the side of the room. NOW.'"
					print 
					print "The guards hesitate and then drop their guns slowly. They back away toward a far wall."
					print "Everyone is staring at you."
					print
					print '-' * 30
					print "1. Ask for the Vault key."
					print "2. Let go of Alison's hand and try to pick up one of the handguns dropped by the guards."
					ini13 = raw_input("> ")
					print '-' * 30
					if ini13 == '1':
						print "You yell out, 'Give me the damn vault key or this innocent girl dies today.'"
						print "The room is silent."
						print "The guards are standing against the wall with their hands in the air."
						print '-' * 30
						print "1. Demand for the Vault key again."
						print "2. Let go of Alison's hand and leap toward one of the handguns left on the floor."
						print "3. Hit Alison."
						ini14 = raw_input("> ")
						if ini14 == '1':
							print "You yell even louder, 'GIVE ME THE FUCKING KEY OR SHE DIES IN 5... 4..."
							print "One of the guards give in."
							print "Guard: 'OK OK here take my key. Just don't hurt her'"
							print "You drag Alison out of the teller window which is just big enough to pull her through."
							print "You walk with Alison toward the guard and take a card from his hand that reads Vault Key."
							inv.add_item('VaultKey')
							print 
							print '-' * 30
							print "1. With the key and Alison, head into the Vault."
							print "2. Let go of Alison's hand and walk into the Vault."
							ini15 = raw_input("> ")
							if ini15 == '1':
								print "You walk backwards toward the Vault holding Alison in front of you as a hostage."
								print "You let go of Alison and she runs out the bank. As you realize you have limited time,"
								print "you turn toward the vault."
								return 'vault'
							if ini15 == '2':
								print "You let go of Alison's hand and run toward the Vault. One of the guards pulls out a"
								print "taser and shoots you with it. You feel three needles pierce through your back and a"
								print "sharp jolt renders your legs immobile. You drop to your knees and begin convulsing"
								print "and foam escapes your lips. Your eyes roll backwards as you go into shock. Your mission"
								print "has failed."
								return 'death'
					if ini13 =='2':
						print "You let go of Alison's hand and jump to pick up one of the loaded handguns that"
						print "the guards dropped on the floor. Your jump isn't far enough so you have to crawl"
						print "an additional step toward the gun. Clumsy move. Amidst the scrambling, one of the"
						print "guards take out a small taser from their vest and shoot at you."
						print 
						print "You feel three needles pierce through your shoulder and a sharp jolt renders your arms immobile."
						print "You drop to your chest and begin convulsing and foam escapes from your lips. Your eyes roll" 
						print "backwards as you go into shock. Your mission has failed."
						return 'death'"
				if ini12 == '2':
					print "You yell at the guards to get their asses in the vault and give you all the cash thats inside."
					print "One of the guards start to walk toward the vault and swipe their card. The vault door opens."
					print
					print "The guard enters the vault momentarily and comes out with two bags of cash worth $1M each."
					print "He throws each bag of cash on the ground."
					print '-' * 30
					print "1. Take one bag and run out the door."
					print "2. Take both bags and run out the door."
					ini16 = raw_input("> ")
					if ini16 == '1':
						print "You let go of Alison's hand and run toward the bags of cash."
						print "As you try to pick up one of the bags, the Guard does a sweet jumping roundhouse kick"
						print "and slams you on the head. You drop to the ground with a broken neck."
						return 'death'
					if ini16 == '2':
						print "You let go of Alison's hand and run toward the bags of cash."
						print "You drop your weapon as you try to pick up the two bags of cash and the Guard pulls out"
						print "a taser and shoots you in the chest. You feel three needles pierce your nipples and neck."
						print "A sharp jolt renders your legs immobile. You drop to your knees and begin convulsing. Foam"
						print "escapes through your lips. Your eyes roll backwards as you go into shock. Your vision fades.."
						return 'death'
			if ini11 == '2':
				
				
		if choice == "3":
			pass
			
		if choice == "4":
			if 'Wallet' in inv.items:
				print "That's a really nice Looey Viddon wallet!"
			pass
	
class SecurityRoom(Scene):
	def enter(self):
		if 'Unmasked' in inv.items:
			print "You approach the Security Room unmasked."
		pass

class Vault(Scene):
	def enter(self):
		print "You made it in front of the Vault. The only thing between you and riches is a gate that"
		print "is controlled by a key machine."
		print
		if 'VaultKey' in inv.items:
			inv.reset_items()
			print "Approaching the key machine, you slide the Vault Key in the electronic receptacle."
			print "The machine beeps and the door opens leading into the Vault. In the vault, there lies"
			print "$20M in cash and a small box with a key hole."
			
	
class PresidentsOffice(Scene):
	def enter(self):
		if 'Unmasked' in inv.items:
			print "You approach the Security Room unmasked."
		pass
	
class EscapeVan(Scene):
	pass
	
class Death(Scene):
	def enter(self):
		print "You lose the game. Try again."
		deth = raw_input("Type 'retry' to start over: ")
		inv.reset_items()
		if 'retry' in deth:
			return 'intro'
		else:
			exit()

class Map(object):

	scenes = {
	    'start_room': StartRoom(),
		'intro': Introduction(),
	    'entrance': Entrance(),
	    'teller': Teller(),
	    'security_room': SecurityRoom(),
	    'vault': Vault(),
	    'presidents_office': PresidentsOffice(),
	    'escape_van': EscapeVan(),
		'death': Death()
	    }

	def __init__(self, start_scene):
		self.start_scene = start_scene
	
	def next_scene(self, scene_name):
		self.scene_name = scene_name
		val = Map.scenes.get(scene_name)
		return val
		
	def opening_scene(self):
		return self.next_scene(self.start_scene)

inv = inventoryClass.inv
a_map = Map('intro')
a_game = Engine(a_map)
a_game.play()
