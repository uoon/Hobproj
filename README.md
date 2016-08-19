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
			print "2. Offer to buy the guards one hotdog each."
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
		if 'Uniform' in inv.items:
			print "You walk out to the lobby with an officer's uniform on. You have no problem"
			print "walking to the Vault."
			return 'vault'
		else:
			print "You enter the lobby and see white marble floors, brightly lit from the crystal"
			print "blue lights gleaming upon each structural slab pillar with gallant pictures of "
			print "global leaders upon the walls. You notice a portrait of Donald Trump on the wall."
			print
			print "To your left, you see a caged door that leads into the Security Room."
			print "To your right, you see some men in uniform transporting a pallet into a corridor,"
			print "and a silver tag on the pallet says, 'Vault'"
			print
			print "You walk up to the teller. The teller is a fair blonde asian with platinum blonde hair."
			print "She looks at you with kindness in her eyes."
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
			print "5. Head over to the Security Room"
			print "6. Head over to the President's Office"
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
						print "Alison: 'The President's Room is next to the Security Room. But the President called"
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
					inv.remove_item('Wallet')
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
						print "2. fill this in."
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
						print "You blurt out, 'OK, calm down. I'm just playing around. Can't a guy joke with'"
						print "a pretty girl?'"
						print 
						print "Alison writes something down and hands you a folded piece of paper."
						print '-' * 30
						print "1. Read the piece of paper."
						print "2. Ignore the note and walk toward the Security Room."
						print "3. Thank Alison and walk toward the exit."
						print
						print '-' * 30
						ini23 = raw_input("> ")
						if ini23 == '1':
							print "You open up the folded note and it reads 'Not a love note. Sike! I don't affiliate"
							print "with criminals. That mask is illegal since the group 'Anonymous' leaked"
							print "nude photos of Donald Trump on the internet. Do you live under a rock?"
							print "You feel something grab you by your wrist."
							print "'You're under arrest, scum.'"
							return 'death'
						if ini23 == '2':
							print "Acknowledging the presence of danger, you realize that you should get moving."
							print "You leave the teller, circle around a line of customers, and then"
							print "You make a break toward the Security Room."
							return 'security_room'
						if ini23 == '3':
							print "You wink at Alison and turn around toward the exit. The guards start "
							print "to pick up their pace to a slight jog. You run toward the exit and leave"
							print "the bank and you see the SUV parked waiting for you. You get in the van and leave."
							print 
							print "While in the van, You open the folded note and it reads:"
							print "'Sike! I don't affiliate with criminals. That mask is illegal since the group"
							print "'Anonymous' leaked nude photos of Donald Trump on the internet. Do you live under"
							print "a rock?' You feel a wave of embarassment and the feeling of regret fills your chest."
							return 'escape_van'
					
					if ini8 == '3':
						print "You reach in through the teller window and get a hold of her wrist. You feel your",
						inv.print_items()
						print "slip out of your pocket."
						print
						print "You hear whispering in the lobby and the volume escalates. You begin to hear gasps."
						print "The customers see your weapon on the ground."
						print '-' * 30
						print "Alison jerks back and yells, 'LET GO OF ME! HELP!!'"
						print "1. Pull Alison through the teller window."
						print "2. Demand Alison to open the register."
						ini17 = raw_input ("> ")
						if ini17 == '1':
							print "You notice that the teller glass has a wide enough opening to pull Alison through."
							print "With all your might, you pull on Alison's wrist and she is in such a panic that"
							print "she does not resist you. The Security Room door slams open and three guards come running"
							print "out with handguns drawn."
							print 
							print "Holding Alison in front of you, you weigh your few options."
							print '-' * 30
							print "1. Tell the guards to drop their handguns and move to the side of the lobby."
							print "2. Demand the guards to go into the Vault and empty out all the inventory in a bag."
							ini18 = raw_input("> ")
							print '-' * 30
							if ini18 == '1':
								print "You yell, 'Drop the fuckin' weapons and move to the side of the room. NOW.'"
								print 
								print "The guards hesitate and then drop their guns slowly. They back away toward a far wall."
								print "Everyone is staring at you."
								print
								print '-' * 30
								print "1. Ask for the Vault key."
								print "2. Let go of Alison's hand and try to pick up one of the handguns dropped by the guards."
								ini19 = raw_input("> ")
								print '-' * 30
								if ini19 == '1':
									print "You yell out, 'Give me the damn vault key or this innocent girl dies today.'"
									print "The room is silent."
									print "The guards are standing against the wall with their hands in the air."
									print '-' * 30
									print "1. Demand for the Vault key again."
									print "2. Let go of Alison's hand and leap toward one of the handguns left on the floor."
									print "3. Hit Alison."
									ini20 = raw_input("> ")
									if ini20 == '1':
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
										ini21 = raw_input("> ")
										if ini21 == '1':
											print "You walk backwards toward the Vault holding Alison in front of you as a hostage."
											print "You let go of Alison and she runs out the bank. As you realize you have limited time,"
											print "you turn toward the vault."
											return 'vault'
										if ini21 == '2':
											print "You let go of Alison's hand and run toward the Vault. One of the guards pulls out a"
											print "taser and shoots you with it. You feel three needles pierce through your back and a"
											print "sharp jolt renders your legs immobile. You drop to your knees and begin convulsing"
											print "and foam escapes your lips. Your eyes roll backwards as you go into shock. Your mission"
											print "has failed."
											return 'death'
								if ini19 =='2':
									print "You let go of Alison's hand and jump to pick up one of the loaded handguns that"
									print "the guards dropped on the floor. Your jump isn't far enough so you have to crawl"
									print "an additional step toward the gun. Clumsy move. Amidst the scrambling, one of the"
									print "guards take out a small taser from their vest and shoot at you."
									print 
									print "You feel three needles pierce through your shoulder and a sharp jolt renders your arms immobile."
									print "You drop to your chest and begin convulsing and foam escapes from your lips. Your eyes roll" 
									print "backwards as you go into shock. Your mission has failed."
									return 'death'
							if ini18 == '2':
								print "You yell at the guards to get their asses in the vault and give you all the cash thats inside."
								print "One of the guards start to walk toward the vault and swipe their card. The vault door opens."
								print
								print "The guard enters the vault momentarily and comes out with two bags of cash worth $1M each."
								print "He throws each bag of cash on the ground."
								print '-' * 30
								print "1. Take one bag and run out the door."
								print "2. Take both bags and run out the door."
								ini22 = raw_input("> ")
								if ini22 == '1':
									print "You let go of Alison's hand and run toward the bags of cash."
									print "As you try to pick up one of the bags, the Guard does a sweet jumping roundhouse kick"
									print "and slams you on the head. You drop to the ground with a broken neck."
									return 'death'
								if ini22 == '2':
									print "You let go of Alison's hand and run toward the bags of cash."
									print "You drop your weapon as you try to pick up the two bags of cash and the Guard pulls out"
									print "a taser and shoots you in the chest. You feel three needles pierce your nipples and neck."
									print "A sharp jolt renders your legs immobile. You drop to your knees and begin convulsing. Foam"
									print "escapes through your lips. Your eyes roll backwards as you go into shock. Your vision fades.."
									return 'death'
							
						if ini17 == '2':
							print "You yell at Alison to open the register or you will explode a bomb strapped to your underwear."
							print "Alison looks at you in disbelief but she complies."
							print
							print "Alison: 'Here, this is all I have in my register.'"
							print "She places $5,000 in front of you."
							print '-' * 30
							print "1. Take the cash and try to escape."
							print "2. $5K is not enough. Demand more money from adjacent registers."
							ini19 = raw_input("> ")
							if ini19 == '1':
								inv.add_item('5k')
								print "You grab the cash and put it in your jacket before you raise your"
								print "hands in the air. The Guards are walking towards you cautiously with"
								print "their weapons drawn. "
								print 
								print "You yell, 'I mean no harm!'"
								print "The guards continue to cautiously advance toward you."
								print '-' * 30
								ini20 = raw_input("> ")
								print "1. Try to distract the guards and run."
								print "2. Turn around and run toward the exit."
								if ini20 == '1':
									print "You yell to the guards, 'My partner is right behind you!'"
									print "The guards turn around and see a wall of customers nervously looking toward the scene."
									print "The guards try to find someone who looks like your accomplice."
									print "Now's your chance."
									print "-" * 30
									print "1. Run out of the bank."
									print "2. Demand more money from Alison."
									if ini21 == '1':
										print "You assess that the only chance you'll make it out alive is to escape."
										print "With the $5,000 in cash, you quickly run toward the door. You were wearing"
										print "Yeezy's which has a surprisingly quiet sole and the Guards, busy searching,"
										print "do not notice you leaving the Bank."
										print "You open the door and notice the SUV parked on the curb."
										return 'escape_van'
									if ini21 == '2':
										print "You demand more money from Alison."
										print "The Guards take it as an escalating threat and they open fire and hit you in the leg."
										print "You scream in pain and drop to your knees. Blood pools around you and you realize that"
										print "you have no way to defend yourself. The Guards approach and tackle you on the ground."
										print 
										print "Guards: 'YOU'RE UNDER ARREST, DOUCHEBAG'"
										return 'death'			
								if ini20 == '2':
									print "You realize your best shot at seeing another day is to leave."
									print "You make a run toward the exit, press open the massive door, and"
									print "the warm humid air feels thick and heavy. You're instantly filled with"
									print "regret. You see the SUV parked on the curb. You run down the steps and"
									print "open the door to your escape."
									return 'escape_van'
							if ini19 == '2':
								print
								print "You put your life at risk so that you can start trading again. "
								print "Is $5,000 enough? No it isn't!"
								print
								print "While acknowledging the impending danger, you demand that Alison opens"
								print "the registers of the nearby tellers and give you more money."
								print "Alison looks back at you with fear. She doesn't have the keys for those."
								print 
								print "Alison: 'I'm ... I'm so sorry. I can't!"
								print "-" * 30
								print "1. Try to grab the cash and run."
								print "2. Demand that she opens the register again."
								ini24 = raw_input("> ")
								if ini24 == '1':
									print "You grab the cash and try to make a break for the exit. It's too late."
									print "The guards are only a few steps behind you and as you turn around, you"
									print "feel a staggering jolt running down your chest. One of the guards open fired"
									print "and hit you in your lungs. Gasping for air, you grab your chest and heave your"
									print "last breath."
									return 'death'
								if ini24 == '2':
									print "You tell Alison, 'I Swear to GOD I WILL KILL YOU IF YOU DON'T OPEN THE REG..'"
									print "Before you know it, One of the guards open fire and you feel a sharp thud"
									print "against your spine. Gasping for air, you grab your chest and heave your"
									print "last breath."
									return 'death'
										
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
							return 'death'
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
					print "The Security Office opens and two guards come walking your way."
					print 
					print "Alison: 'I'm so sorry... I had to report you. The mask you are carrying"
					print "is illegal. My career is on the line! I hope you understand..."
					print
					print "Guards ask you to remove the mask and come with them as you are under arrest."
					return 'death'
					
			if choice == '3':
				inv.remove_item('Wallet')
				inv.remove_item('Uniform')
				print "Without saying a word, you strike her with your"
				inv.print_items()
				print "."
				print 
				print "Alison falls to the ground with a bloody gash clean across her forehead."
				print "Customers in line notice what you've done and everyone begins to scream."
				print "The door to the Security room busts open and Guards come running out the door."
				print "Guards enter through the entrance with hotdogs in one hand and a handgun in the other"
				print "You realize that you are pretty much screwed. Live or die, you are not getting out of"
				print "this before a life-time sentence."
				return 'death'

				
			if choice == '4':
				if 'Wallet' in inv.items:
					print "'I really love your pendant, Alison.'"
					print "Alison looks down at the pendant. Her gaze returns to you."
					print "Alison: 'My mother gave it to me before she left to join the Anonymous war."
					print "By the way, you DO know that the mask you have on is illegal ever since"
					print "Anonymous leaked nude pictures of Donald Trump on the internet? You should take it off."
					print "-" * 30
					print "1. Keep the mask on and continue talking."
					print "2. Take off the mask and continue talking."
					ini25 = raw_input("> ")
					if ini25 == '1':
						print
						print "You decide to keep the mask on."
						print
						print "'Hey, I am just getting ready for the next Anonymous war. Maybe I will see"
						print "your mom and tell her what a fine daughter she's raised. If your mom is half"
						print "as beautiful as you, she could take over a country just with her smile."
						print 
						print "Alison's eyes narrow and her eyebrows furrow closer."
						print
						print "Alison: 'My mother was murdered by the military while they attempted to prevent a coup."
						print "Even though she joined Anonymous, she fought for what she believed was right and she despised"
						print "the men who were in it because they only cared about getting in bed with her. You remind me of"
						print "the men she hated.'"
						print 
						print "-" * 30
						print "1. 'I'm sorry, I didn't mean to offend you.'"
						print "2. 'Your mom raised you wrong. That's not what all men who hit on girls in public think.'"
						ini26 = raw_input("> ")
						if ini26 == '1':
							print "'I'm sorry, I didn't mean to offend you.'"
							print "Alison's expression does not change"
							print 
							print "Alison: 'I don't care what you meant or didn't mean. I've alerted the guards and they're"
							print "coming now. You can leave or stay and be arrested.'"
							print
							print '-' * 30 
							print "1. Leave the bank."
							print "2. Stay and try to reason with Alison."
							ini27 = raw_input("> ")
							if ini27 == '1':
								print "You see guards coming out of the Security Room. You decide that it's probably best"
								print "that you leave the bank before things escalate further. You turn around and run toward"
								print "the exit. You press open the door and the hear the noise of pouring rain as you leave"
								print "the bank with no reward other than avoiding arrest."
								return 'escape_van'
							if ini27 == '2':
								print "You try and reason with Alison further."
								print
								print "In the middle of another word, you feel someone grab your shoulder and turn you around."
								print "Alison called the security guards and they grab your mask and pull it off your face."
								print "Guard: 'You're under arrest for carrying an illegal mask banned by national law."
								print
								print "You realize that it is the bitter end."
								return 'death'
						if ini26 == '2':
							print "You feel offended. You're not a creep! You just want love! Maybe you would even castrate"
							print "yourself if it meant that you would find the love of your life. You get angry."
							print 
							print "'What the hell are you talking about? Don't just generalize some men your mother has met with"
							print "all men! I'm through with you. I'm filing a complaint against your conduct. GOOD DAY!'"
							print 
							print "You forget why you even came into the bank in the first place and you storm out of the lobby"
							print "and go outside. The SUV is parked waiting for you."
							return 'escape_van'
					if ini25 == '2':
						print 
						print "You decide to go along with her and take off your mask."
						print "Alison looks at you and is instantly attracted to your handsome face. She blushes."
						print
						inv.add_item('Unmasked')
						print "Alison: 'Hey... thanks for taking off your mask.. my mom gave me this pendant before"
						print "she joined the Anonymous war and she has never returned. This is what I remember her by.'"
						print 
						print "Alison: 'So.. do you need to make a withdrawal or.. did you want to ask me something?"
						print "-" * 30
						print "1. Make a withdrawal."
						print "2. Ask Alison for her number."
						ini28 = raw_input(" > ")						
						if ini28 == '1':
							print "'Hello Alison, I'd like to make a withdrawal.'"
							print '-' * 30
							print "Alison's smile retreats slightly."
							print
							print "Alison: 'Sure, I can help you with that... '"
							print '-' * 30
							print "1. 'I don't have time for this. Give me all the money in your register.'"
							print "2. Remain silent."
							print '-' * 30
							ini40 = raw_input("> ")
							if in40 == '1':
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
								ini41 = raw_input("> ")
								if ini41 == '1':
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
								if ini41 == '2':
									inv.remove_item('Wallet')
									print "You demand the key to the Vault with the assumption that there is more money"
									print "inside. Alison begins to explain that only the President has the key and starts"
									print "to cry. The tellers start backing away from your direction and customers begin"
									print "to pack up their belongings and walk quickly toward the exit. Time is running out."
									print 
									print "Alison: 'The President's Room is next to the Security Room. But the President called"
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
								if ini41 == '3':
									print "Without even collecting the money, you run toward the Security Room."
									return 'security_room'
								if ini41 == '4':
									print "Without even grabbing the money, you run toward the President's Office"
									return 'presidents_office'
													
							if ini40 == '2':
								print "You stand there silently as Alison appears to get increasing uncomfortable."
								print
								print "Alison: Ok fine. Just don't say anything, will you? I'm going to call security."
								print
								print "You see her reaching toward a switch underneathe the desk."
								print "Time slows down."
								print
								inv.remove_item('Wallet')
								print "1. While remaining silent, slowly reveal your",
								inv.print_items()
								print
								print "2. Give in to the pressure and respond, 'Ok you got me. Don't report me.'"
								print "3. Reach in through the teller window and grab Alison's hand."
								ini42 = raw_input("> ")
								if ini42 == '1':
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
									print "2. Leave Alison only to return to her in 5 minutes."
									ini43 = raw_input("> ")
									if ini43 == '1':
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
										ini44 = raw_input("> ")
										if ini44 == '1':
											print "You open up the folded note and it reads 'Sike! I don't affiliate"
											print "with criminals. That mask is illegal since the group 'Anonymous' leaked"
											print "nude photos of Donald Trump on the internet. Do you live under a rock?"
											print "You feel something grab you by your wrist."
											print "'You're under arrest, scum.'"
											return 'death'
										if ini44 == '2':
											print "Acknowledging the presence of danger, you realize that you should get moving."
											print "You leave the teller, circle around a line of customers, and then"
											print "You make a break toward the Security Room."
											return 'security_room'
										if ini44 == '3':
											print "You wink at Alison and turn around toward the exit. The guards start "
											print "to pick up their pace to a slight jog. You run toward the exit and leave"
											print "the bank and you see the SUV parked waiting for you. You get in the van and leave."
											print 
											print "While in the van, You open the folded note and it reads:"
											print "'Sike! I don't affiliate with criminals. That mask is illegal since the group"
											print "'Anonymous' leaked nude photos of Donald Trump on the internet. Do you live under"
											print "a rock?' You feel a wave of embarassment and the feeling of regret fills your chest."
											return 'escape_van'
									if ini43 == '2':
										return 'teller'
								if ini42 == '2':
									print "You blurt out, 'OK, calm down. I'm just playing around. Can't a guy joke with'"
									print "a pretty girl?'"
									print 
									print "Alison writes something down and hands you a folded piece of paper."
									print '-' * 30
									print "1. Read the piece of paper."
									print "2. Ignore the note and walk toward the Security Room."
									print "3. Thank Alison and walk toward the exit."
									print
									print '-' * 30
									ini45 = raw_input("> ")
									if ini45 == '1':
										print "You open up the folded note and it reads 'Not a love note. Sike! I don't affiliate"
										print "with criminals. That mask is illegal since the group 'Anonymous' leaked"
										print "nude photos of Donald Trump on the internet. Do you live under a rock?"
										print "You feel something grab you by your wrist."
										print "'You're under arrest, scum.'"
										return 'death'
									if ini45 == '2':
										print "Acknowledging the presence of danger, you realize that you should get moving."
										print "You leave the teller, circle around a line of customers, and then"
										print "You make a break toward the Security Room."
										return 'security_room'
									if ini45 == '3':
										print "You wink at Alison and turn around toward the exit. The guards start "
										print "to pick up their pace to a slight jog. You run toward the exit and leave"
										print "the bank and you see the SUV parked waiting for you. You get in the van and leave."
										print 
										print "While in the van, You open the folded note and it reads:"
										print "'Sike! I don't affiliate with criminals. That mask is illegal since the group"
										print "'Anonymous' leaked nude photos of Donald Trump on the internet. Do you live under"
										print "a rock?' You feel a wave of embarassment and the feeling of regret fills your chest."
										return 'escape_van'
								
								if ini42 == '3':
									print "You reach in through the teller window and get a hold of her wrist. You feel your",
									inv.print_items()
									print "slip out of your pocket."
									print
									print "You hear whispering in the lobby and the volume escalates. You begin to hear gasps."
									print "The customers see your weapon on the ground."
									print '-' * 30
									print "Alison jerks back and yells, 'LET GO OF ME! HELP!!'"
									print "1. Pull Alison through the teller window."
									print "2. Demand Alison to open the register."
									ini46 = raw_input ("> ")
									if ini46 == '1':
										print "You notice that the teller glass has a wide enough opening to pull Alison through."
										print "With all your might, you pull on Alison's wrist and she is in such a panic that"
										print "she does not resist you. The Security Room door slams open and three guards come running"
										print "out with handguns drawn."
										print 
										print "Holding Alison in front of you, you weigh your few options."
										print '-' * 30
										print "1. Tell the guards to drop their handguns and move to the side of the lobby."
										print "2. Demand the guards to go into the Vault and empty out all the inventory in a bag."
										ini46 = raw_input("> ")
										print '-' * 30
										if ini46 == '1':
											print "You yell, 'Drop the fuckin' weapons and move to the side of the room. NOW.'"
											print 
											print "The guards hesitate and then drop their guns slowly. They back away toward a far wall."
											print "Everyone is staring at you."
											print
											print '-' * 30
											print "1. Ask for the Vault key."
											print "2. Let go of Alison's hand and try to pick up one of the handguns dropped by the guards."
											ini47 = raw_input("> ")
											print '-' * 30
											if ini47 == '1':
												print "You yell out, 'Give me the damn vault key or this innocent girl dies today.'"
												print "The room is silent."
												print "The guards are standing against the wall with their hands in the air."
												print '-' * 30
												print "1. Demand for the Vault key again."
												print "2. Let go of Alison's hand and leap toward one of the handguns left on the floor."
												print "3. Hit Alison."
												ini47 = raw_input("> ")
												if ini48 == '1':
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
													ini48 = raw_input("> ")
													if ini48 == '1':
														print "You walk backwards toward the Vault holding Alison in front of you as a hostage."
														print "You let go of Alison and she runs out the bank. As you realize you have limited time,"
														print "you turn toward the vault."
														return 'vault'
													if ini48 == '2':
														print "You let go of Alison's hand and run toward the Vault. One of the guards pulls out a"
														print "taser and shoots you with it. You feel three needles pierce through your back and a"
														print "sharp jolt renders your legs immobile. You drop to your knees and begin convulsing"
														print "and foam escapes your lips. Your eyes roll backwards as you go into shock. Your mission"
														print "has failed."
														return 'death'
											if ini47 =='2':
												print "You let go of Alison's hand and jump to pick up one of the loaded handguns that"
												print "the guards dropped on the floor. Your jump isn't far enough so you have to crawl"
												print "an additional step toward the gun. Clumsy move. Amidst the scrambling, one of the"
												print "guards take out a small taser from their vest and shoot at you."
												print 
												print "You feel three needles pierce through your shoulder and a sharp jolt renders your arms immobile."
												print "You drop to your chest and begin convulsing and foam escapes from your lips. Your eyes roll" 
												print "backwards as you go into shock. Your mission has failed."
												return 'death'
										if ini46 == '2':
											print "You yell at the guards to get their asses in the vault and give you all the cash thats inside."
											print "One of the guards start to walk toward the vault and swipe their card. The vault door opens."
											print
											print "The guard enters the vault momentarily and comes out with two bags of cash worth $1M each."
											print "He throws each bag of cash on the ground."
											print '-' * 30
											print "1. Take one bag and run out the door."
											print "2. Take both bags and run out the door."
											ini50 = raw_input("> ")
											if ini50 == '1':
												print "You let go of Alison's hand and run toward the bags of cash."
												print "As you try to pick up one of the bags, the Guard does a sweet jumping roundhouse kick"
												print "and slams you on the head. You drop to the ground with a broken neck."
												return 'death'
											if ini50 == '2':
												print "You let go of Alison's hand and run toward the bags of cash."
												print "You drop your weapon as you try to pick up the two bags of cash and the Guard pulls out"
												print "a taser and shoots you in the chest. You feel three needles pierce your nipples and neck."
												print "A sharp jolt renders your legs immobile. You drop to your knees and begin convulsing. Foam"
												print "escapes through your lips. Your eyes roll backwards as you go into shock. Your vision fades.."
												return 'death'
										
									if ini46 == '2':
										print "You yell at Alison to open the register or you will explode a bomb strapped to your underwear."
										print "Alison looks at you in disbelief but she complies."
										print
										print "Alison: 'Here, this is all I have in my register.'"
										print "She places $5,000 in front of you."
										print '-' * 30
										print "1. Take the cash and try to escape."
										print "2. $5K is not enough. Demand more money from adjacent registers."
										ini53 = raw_input("> ")
										if ini53 == '1':
											inv.add_item('5k')
											print "You grab the cash and put it in your jacket before you raise your"
											print "hands in the air. The Guards are walking towards you cautiously with"
											print "their weapons drawn. "
											print 
											print "You yell, 'I mean no harm!'"
											print "The guards continue to cautiously advance toward you."
											print '-' * 30
											ini54 = raw_input("> ")
											print "1. Try to distract the guards and run."
											print "2. Turn around and run toward the exit."
											if ini54 == '1':
												print "You yell to the guards, 'My partner is right behind you!'"
												print "The guards turn around and see a wall of customers nervously looking toward the scene."
												print "The guards try to find someone who looks like your accomplice."
												print "Now's your chance."
												print "-" * 30
												print "1. Run out of the bank."
												print "2. Demand more money from Alison."
												if ini55 == '1':
													print "You assess that the only chance you'll make it out alive is to escape."
													print "With the $5,000 in cash, you quickly run toward the door. You were wearing"
													print "Yeezy's which has a surprisingly quiet sole and the Guards, busy searching,"
													print "do not notice you leaving the Bank."
													print "You open the door and notice the SUV parked on the curb."
													return 'escape_van'
												if ini55 == '2':
													print "You demand more money from Alison."
													print "The Guards take it as an escalating threat and they open fire and hit you in the leg."
													print "You scream in pain and drop to your knees. Blood pools around you and you realize that"
													print "you have no way to defend yourself. The Guards approach and tackle you on the ground."
													print 
													print "Guards: 'YOU'RE UNDER ARREST, DOUCHEBAG'"
													return 'death'			
											if ini54 == '2':
												print "You realize your best shot at seeing another day is to leave."
												print "You make a run toward the exit, press open the massive door, and"
												print "the warm humid air feels thick and heavy. You're instantly filled with"
												print "regret. You see the SUV parked on the curb. You run down the steps and"
												print "open the door to your escape."
												return 'escape_van'
										if ini53 == '2':
											print
											print "You put your life at risk so that you can start trading again. "
											print "Is $5,000 enough? No it isn't!"
											print
											print "While acknowledging the impending danger, you demand that Alison opens"
											print "the registers of the nearby tellers and give you more money."
											print "Alison looks back at you with fear. She doesn't have the keys for those."
											print 
											print "Alison: 'I'm ... I'm so sorry. I can't!"
											print "-" * 30
											print "1. Try to grab the cash and run."
											print "2. Demand that she opens the register again."
											ini56 = raw_input("> ")
											if ini56 == '1':
												print "You grab the cash and try to make a break for the exit. It's too late."
												print "The guards are only a few steps behind you and as you turn around, you"
												print "feel a staggering jolt running down your chest. One of the guards open fired"
												print "and hit you in your lungs. Gasping for air, you grab your chest and heave your"
												print "last breath."
												return 'death'
											if ini56 == '2':
												print "You tell Alison, 'I Swear to GOD I WILL KILL YOU IF YOU DON'T OPEN THE REG..'"
												print "Before you know it, One of the guards open fire and you feel a sharp thud"
												print "against your spine. Gasping for air, you grab your chest and heave your"
												print "last breath."
												return 'death'
								
						if ini28 == '2':
							print "You ask Alison for her number and she looks down and back into your eyes."
							print "Alison: 'Do you have something to write with?'"
							print
							print "You accidentally pull out the wallet given to you by the Guards outside."
							print "Alison's eyes widen with surprise."
							print 
							print "Alison: 'Wow. That's a beautiful wallet. You must be rich. My mom told me that once I find"
							print "a man that I want to be with for the rest of my gold-digging life, I should give this to the man"
							print "immediately. It is made with some type of electrostatic gel that when exposed to oxygen in the"
							print "air, it can turn off electronics within a 1 foot viscinity. If I give you this, promise to take "
							print "me out on a date afterwards?"
							print "-" * 30
							print "1. You sure you want to give it to me?"
							print "2. I'll take your offer babe."
							ini29 = raw_input("> ")
							if ini29 == '1':
								print "Alison replies, 'On second thought.. I shouldn't offer this precious pendant to someone"
								print "who second guesses an offer. Sorry you're not the one. I'm calling the police because I think"
								print "you actually stole that wallet. Plus, you have that illegal mask with you. I'm sorry.'"
								print 
								print "The Security Room door slams open and three guards come out heading your direction."
								print "There is nowhere to run and you realize that you messed up, badly."
								return 'death'
							if ini29 == '2':
								print "Alison replies, 'Here take it hubby bubby.'"
								print "Pendant was added to your inventory."
								inv.add_item('Pendant')
								print "Alison: 'Now, what else can I do for YOU Mr. Spectacular?'"
								print '-' * 30
								print "1. Ask her about the President of the bank."
								print "2. Ask her about the lack of security at the Bank."
								ini30 = raw_input("> ")
								if ini30 == '1':
									print "You casually ask about how much the President of the bank much make on an annual basis."
									print "'So, the president must make enough income to afford beautiful things like your pendant!"
									print "Alison blushes at you."
									print "Alison: 'I am not dating the President. He's married. I think he is sick though. I didn't"
									print "see him here today."
									print
									print "'I'm sorry Alison, but I have to use the restroom. Mind if I come back to you?'"
									print "Alison nods and waves her hand signaling for the next customer."
									print '-' * 30
									print "1. Walk over to the President's Office."
									print "2. Ask Alison about the lack of security at the Bank."
									print '-' * 30
									ini31 = raw_input("> ")
									if ini31 == '1':
										print "You walk over to the President's Office."
										return 'presidents_office'
									if ini31 == '2':
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
										ini32 = raw_input("> ")
										if ini32 == '1':
											print "You walk over to the President's Office."
											return 'presidents_office'
										if ini32 == '2':
											print "You walk over to the Security Room"
											return 'security_room'
								if ini30 == '2':
									print "You ask Alison, 'So, what's the deal with the lack of security at this bank?"
									print "Isn't this bank known to carry most of the wealth of the nation?"
									print
									print "Alison looks at you strangely."
									print
									print "Alison: Well, yes, but the security guards are usually in their rooms trying to"
									print "guess what the President's wife looks like. Apparently she married Donald Trump"
									print "and took half his wealth, reinvested it in the stock market, and is now one of "
									print "the world's richest women that has never been seen on media since Trump made it"
									print "against the law to for her to appear in public."
									print 
									print '-' * 30
									print "1. Ask her about the President of the bank."
									print "2. Walk over to the Security Office."
									ini33 = raw_input("> ")
									if ini33 == '1':
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
										ini34 = raw_input("> ")
										if ini34 == '1':
											print "You walk over to the President's Office."
											return 'presidents_office'
										if ini34 == '2':
											print "You walk over to the Security Room"
											return 'security_room'
									if ini33 == '2':
										print "You walk over to the President's Office."
										return 'presidents_office'
									
				else:
					print "You try to compliment Alison but you see flash backs of getting rejected in when trying to "
					print "hit on girls following some YuuTube videos on how to pick up girls."
					print "You choke on your own saliva and words don't come out."
					print "Alison looks increasingly concerned and pushes a button below her counter."
					print "Guards come walking out of the security room and you realize you cannot go on with your mission."
					return 'death'
			if choice == '5':
				print "You walk over to the Security Room."
				return 'security_room'
			if choice == '6':
				print "You walk toward the President's Office."
				return 'presidents_office'
class SecurityRoom(Scene):

	def enter(self):
		if 'Unmasked' in inv.items:
			print "You approach the Security Room unmasked."
			print "The door is behind a cage. You can hear people talking inside the room."
			print "You don't think there is any way you can get in unless you have clearance."
			print "-" * 30
			print "1. Head to the President's Office."
			print "2. Head back to the teller."
			print "3. Try to open the door."
			ini35 = raw_input("> ")
			if ini35 == '1':
				return 'presidents_office'
			if ini35 == '2':
				return 'teller'
			if ini35 == '3':
				print "You try to open the door."
				if 'SecurityCard' in inv.items:
					print "You use the SR (Security Card) which scans and the light into the door turns green."
					print "The door opens and you see three guards watching what looks like soft-core porn."
					print "The guards do not notice you standing behind them. You look to the right and theres"
					print "a keyring with a key that reads Vault Key."
					print "-" * 30
					print "1. Ambush the guards by using your weapon as a blunt tool."
					print "2. Leave the room."
					print "3. Take the Vault Key and close the door quietly"
					ini57 = raw_input("> ")
					if ini57 == '1':
						inv.add_item('VaultKey')
						print "You try to jump the guards who are hunched over the monitor. While creeping up,"
						print "you step on a piece of Leyz Chips and the crunch noise startles the guards. They"
						print "turn around and quickly draw their weapons. You put your hands in the air."
						print 
						print "Guard: 'The fuck you think you're doing?'"
						print 
						print "Residue left in your pocket from the pendant messes with the monitor electronics."
						print "The speakers start blasting porn music throughout the lobby and the guards turn around"
						print "in an attempt to stifle the noise. You take this opportunity to kick each of them in the"
						print "groin and they all drop down and die instantly. Wow, that was easy."
						print "-" * 30
						print "1. Return to the teller."
						print "2. Put on one of the Guard's uniform."
						ini58 = raw_input ("> ")
						if ini58 == '1':
							return 'teller'
						if ini58 == '2':
							inv.add_item('Uniform')
							print "You put on the guard uniform and walk outside the Security Room."
							return 'teller'
					if ini57 == '2':
						print
						print "You feel nervous and you decide to return to the teller."
						return 'teller'
					if ini57 == '3':
						print "You quietly turn, take one step, and take the key off the wall. You turn around to"
						print "leave the room and you step on a piece of Leyz Chips and the crunch noise startles"
						print "the guards. They turn around and quickly draw their weapons. You put your hands in "
						print "the air. "
						print "Damn. Mission failed."
						return 'death'
			
		else: 
			print "You approach the Security Room with your mask on."
			print "A camera with red blinking lights tracks your movements toward the door."
			print "In an instant, the door slams open and before you can even react, shots are fired"
			print "from within the room. You feel a sudden impact to your chest and fall unconscious."
			return 'death'

class Vault(Scene):
	def enter(self):
		print "You made it in front of the Vault. The only thing between you and riches is a gate that"
		print "is controlled by a key machine."
		print
		if 'Uniform' in inv.items:
			print "You look around the Vault and nobody finds your movements suspicious."
			print "Try to open the door?"
			print "-" * 30
			print "1. Try to open the door"
			print "2. Return to the teller."
			ini62 = raw_input("> ")
			if ini62 == '1':
				if 'VaultKey' in inv.items:
					print "Approaching the key machine, you slide the Vault Key in the electronic receptacle."
					print "The machine beeps and the door opens leading into the Vault. In the vault, there lies"
					print "$20M in cash and a small box with a combination lock."
					print "1. Take the cash and leave."
					print "2. Attempt to crack the combination lock."
					ini60 = raw_input("> ")
					if ini60 == '1':
						inv.add_item('20m')
						print "You take the $20,000,000 and stuff it into your jacket. Time to get out."
						print "You leave the vault and then leave the bank. You see a SUV parked outside waiting"
						print "for you. You get into the van and you escape safely."
						return 'escape_van'
					if ini60 == '2':
						print "You attempt to crack the code and you succeed. You didn't even have to try. At this"
						print "point I'm exhausted of writing text. You win the best achievable ending with a max"
						print "prize of $30,000,000."
						inv.add_item('30m')
						return 'escape_van'
				else:
					print "You try to open the door but it won't budge. Alarms go off and you find yourself "
					print "royally screwed. I guess thats the end of it. A naked guard runs out of the security room."
					print "Game over."
					return 'death'

			if ini62 == '2':
				print "One of the guards notice you from a camera in the Security Room and presses the"
				print "alarm button. The entire bank goes on lockdown and you find yourself trapped in the"
				print "vault room."
				print
				print "Police are on their way and you have nowhere else to go."
				return 'death'
		else: 
			print "You don't have a key to enter the Vault. There must be another way."
			print "-" * 30
			print "1. Return to the Teller."
			ini61 = raw_input("> ")
			if ini61 == '1':
				return 'teller'
			
		
			
	
class PresidentsOffice(Scene):
	def enter(self):
		if 'Unmasked' in inv.items:
			print "You approach the Security Room unmasked. You don't appear suspicious at all."
			print "The door to the President's Office is open slightly so you look behind you and then"
			print "proceed into the room."
			print "The room is empty except for a large mahogany desk and a small electronic device surrounded"
			print "an electronic field of some sort."
			print "-" * 30
			print "1. Place your hand on the device."
			print "2. Leave the room back to the teller."
			ini36 = raw_input("> ")
			if ini36 == '1':
				print "You place your hand on the electronic device."
				if 'Pendant' in inv.items:
					print "The pendant in your pocket explodes and the electronic field dissapates. The device"
					print "opens and a key card in the box. The card says has the letters 'S.R.' on it."
					print "You obtained the S.R. Key Card."
					inv.add_item('SecurityCard')
					print "-" * 30
					print "There is nothing else of interest in this room."
					print "1. Return to the teller."
					ini37 = raw_input("> ")
					if ini37 == '1':
						inv.remove_item('Pendant')
						return 'teller'
					else: 
						print "Invalid choice. You sit on the table and wonder what to do next."
						ini37 = raw_input("> ")
			if ini36 == '2':
				return 'teller'
			
		else: 
			print "You approach the President's Office with your mask on."
			print "A camera with red blinking lights tracks your movements toward the door."
			print "Before you know what's happening, you hear a door slam open behind you."
			print "Before you can even react, you hear gunshots from behind. Guards from the"
			print "security room open fired. You feel jarring impacts to your back and fall"
			print "to the ground, losing consciousness quickly."
			return 'death'
	
class EscapeVan(Scene):
	def enter(self):
		if '5k' in inv.items:
			pass
		if '10k' in inv.items:
			pass
		if '1m' in inv.items:
			pass
		if '20m' in inv.items:
			pass
		if '30m' in inv.items:
			pass
		else:
			print "You left the bank with nothing. Clinton stares at you in disbelief."
			print "Clinton: 'You made me risk everything for you... and you show me this??'"
			print 
			print "Clinton puts both hands on your cheeks and with a lightning fast twist,"
			print "she breaks your neck. You died."
			return 'death'
	
class Death(Scene):
	def enter(self):
		print "You lose the game. Try again."
		deth = raw_input("Type 'retry' to start over: ")
		inv.reset_items()
		if 'retry' in deth:
			return 'start_room'
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
