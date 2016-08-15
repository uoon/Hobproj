# Bank-Heist

class Engine(object):
	"""Game engine to cycle through play and Map()"""
	
	def __init__(self, scene_map):
		self.scene_map = scene_map
		
	def play(self):
		current_scene = self.scene_map.opening_scene()
		last_scene = self.scene_map.next_scene('escape_van')
		
		while current_scene != last_scene:
			print "\n----------------"
			next_scene_name = current_scene.enter()
			current_scene = self.scene_map.next_scene(next_scene_name)
			
		current_scene.enter()

class Inventory(object): 
"""Need to figure out how to add/change to dict in __init__"""
	
	def __init__(self):
		self.items = {}
	
	def add_item(self, item):
		self.items[item] = item
			
	def remove_item(self, item):
		self.items[item] = item
		del self.items[item]
		
	def print_items(self):
		for item in self.items:
			print item		

class Scene(object): 
	"""This class to cycle through scenes"""	
	
	def enter(self):
		print "This scene is not yet configured. Subclass it and implement enter()"
		exit()

class StartRoom(Scene):
	"""first scene"""

	def enter(self):
		print "Alright, time to gear up."
		print "What weapon will you like to start with?"
		print "1. Club", "2. Knife", "3. Shotgun"
		choice = raw_input("> ")
		inventory = Inventory()
		
		if choice == '1':
			inventory.add_item['Club']
			return 'entrance'
	
		elif choice == '2':
			inventory.add_item['Knife']
			print item, "was added to your inventory!"
			return 'entrance'
	
		elif choice == '3':
			inventory.add_item['Shotgun']
			print item, "was added to your inventory!"
			return 'entrance'
			
		else:
			print "That's not a valid choice."
			inventory.add_item['None']
			return 'entrance'
			
			
class Map(object):
	"""Map class works with Engine class to change scenes"""

	scenes = {
	    'start_room': StartRoom(),
	    'entrance': Entrance(),
	    'teller': Teller(),
	    'security_room': SecurityRoom(),
	    'vault': Vault(),
	    'managers_office': ManagersOffice(),
	    'escape_van': EscapeVan()
	    }

	def __init__(self, start_scene):
		self.start_scene = start_scene
	
	def next_scene(self, scene_name):
		self.scene_name = scene_name
		val = Map.scenes.get(scene_name)
		print "next_scene returns", val
		return val
		
	def opening_scene(self):
		return self.next_scene(self.start_scene)
		
		
inventory = Inventory()
a_map = Map('start_room')
a_game = Engine(a_map)
a_game.play()
