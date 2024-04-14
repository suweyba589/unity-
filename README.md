Video : https://www.youtube.com/watch?v=C-O4H3y6LcE \
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/C-O4H3y6LcE/0.jpg)](https://youtu.be/C-O4H3y6LcE)

Setup \
Inside the Scenes folder (Assets > Scenes > coursework) press the coursework.unity file. \
<img width="164" alt="Screenshot 2024-04-12 at 00 20 03" src="https://github.com/suweyba589/unity-/assets/74510746/9333e72d-848e-445c-9bba-61dbe3190145">  


Assets \
├── Material \
├── NPBehave \
├── Prefab \
├── Scenes \
├── Scripts \
│   ├── GenerateMap.cs \
│   ├── survivorPlayer.cs \
│   ├── Weapon.cs \
│   └── zombiePlayer.cs \
└── README.md 




Level Generator Implementation:

1. Initial 2D Grid Generation (Stage a):
- A predefined probability threshold is used to randomly assign each cell in the initial grid, which has specific dimensions (e.g., 100x100), to either filled (land) or empty (water).

2. Cellular Automata (Stage b):
- Cellular automata rules are applied to the initial grid to simulate natural terrain features like islands and water bodies.
- For example, if a cell has more filled neighbors than empty neighbors, it remains filled (land); otherwise, it becomes empty (water).
- The SmoothMap() method smoothens the generated map to remove noise by adjusting the values based on the number of surrounding land tiles.
- The AddBeaches() method identifies land tiles adjacent to water and marks them as beach tiles.

3. Post-Processing (Stage c):

- After applying cellular automata, the grid undergoes post-processing to add additional environmental features such as trees, the supply house, and weapon.
- The GenerateTrees() method generates clusters of trees on the map based on predefined parameters such as cluster size and density.


Agent Behaviors Implementation:

Agent A (Survivor):
- Behavior tree nodes control the survivor's actions and interactions with the environment. The behavior tree consists of tasks and services such as movement, checking proximity to zombies, water collision, weapon pickup, attacking zombies, and checking health for supply house search.
-  The survivor moves randomly and adjusts it speed based on the terrain.
- The FleeFromZombies node detects nearby zombies and prompts the survivor to flee to safety by finding the shortest path to a secure location.
- If the survivor dies it respawn in a new location.

Agent B (Zombie):
- Same as survivor,the zombie's behavior is controlled by a behavior tree, implemented using NPBehave.The behavior tree includes tasks for movement, checking for obstacles, attacking survivors, and avoiding water.
- The zombie moves towards the nearest survivor while avoiding obstacles, adjusting speed based on terrain (beach or normal land).
- The zombie attacks survivors nearest to it, dealing damage to them.
- If the zombie dies, it respawns at a random position on the map.
