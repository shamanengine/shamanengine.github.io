# Flyer
Raspberry Pi Zero W acting as a brain of the system, encapsulating:
- Web server for communication with Blue Prism
- AI game engine 
- Protocol for communication with the Circut Board

Python web server is running on Raspberry Pi Zero W providing an API for Blue Prism in the format of SOAP web services. API consists of two parts: 
- API for sending commands to Arduino-based controller
- API one for invoking and controlling AI engine

AI engine is using the next key approaches to calculate an optimal move:
- Bitboards - each possible game state is encoded uniquely in the form of two bit strings. This allows to compute operations/ checks more efficiently
- Game tree - every game has a discrete action space (or a finite number of possible actions in every move). A game tree is constructed in which each node represents a possible game state
- Scoring function - each leaf node of a game tree is awarded a certain score
- Minimax algorithm and Alpha-beta pruning - search algorithms that explore game tree and seek optimal move based on the score of a scoring function
