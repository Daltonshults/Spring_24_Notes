
### Initialization:
Initialize the network to compute the prior probabilities (i.e., the probabilities based on the instantiation of no variables) of all variables as follows:  
1. Set all λ-messages and λ-values to 1.  
2. If the root A has m possible values, 
	* then for 1 ≤ j ≤ m, set  P′(aj ) = P(aj ), and set π(aj ) = (aj).  
3. For all children B of the root A, compute a new π-message for B using operative formula 2.  
4. For all children B of the root A, post a new π-message to B using Update Rule C.  
▶ A propagation flow will then begin due to updating in Step D.  
▶ Note that Step B was not in the original algorithm, but seems necessary.


### If instantiated: Update Rule A
If a variable B is instantiated for $b_j$ , then  
1. Set P′(bj ) = 1 and for i ̸ = j, set P′(bi ) = 0.  
2. Compute λ(B) using operative formula 3.  
3. Compute new λ-messages for B’s parent using operative formula 1.  
4. Post the new λ-messages to B’s parent using Update Rule B.  
5. Compute new π-messages for B’s children using operative formula 2.  
6. Post the new π-messages to B’s children using Update Rule C.

### Receives a new $\lambda$-message and not instantiated: Update Rule B
If a variable B receives a new λ-message from one of its children and if B is not already instantiated, then  
1. Compute the new value of λ(B) using operative formula 3.  
2. Compute the new value of P′(B) using operative formula 5.  
3. Compute new λ-messages for B’s parent using operative formula 1.  
4. Post the new λ-messages to B’s parent using Update Rule B.  
5. Compute new π-messages for B’s children using operative formula 2.  
6. Post the new π-messages to B’s other children using Update Rule C.


### Receives new $\pi$-message
If a variable B receives a new π-message from its parent and if B  
is not already instantiated, then  
1. Compute the new value of π(B) using operative formula 4.  
2. Compute the new value of P′(B) using operative formula 5.  
3. Compute new π-messages for B’s children using operative formula 2.  
4. Post the new π-messages to B’s children using Update Rule C.


