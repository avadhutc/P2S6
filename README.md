# P2S6

Pseudo code:
Require:

states X = {1,.....,nx}
actions A = {1,.....,na}, A: X => A
Reward function R: X * A -> R
Black-box(probabilistic) transition function T: X * A -> X
Learning rate alpha belongs to [0,1] typically alpha = 0.1
Discounting factor gamma belongs to [0,1]


Preocedure QLearning(X, A, R, T, alpha, gamma)
	#__init__
	Initialize Q : X * A -> R arbitarily
	while Q is not converged do
		start in state s belongs to X
		while s is not terminal do
			calculate policy according to Q and exploration strategy(e.g. policy(x) <- arg maxa Q(x,a))
			#getQValue
			 getQValue = Q(s, a)
			
			#computeValueFromQValues
			Qn(s, a) = [Q(s, a) for a in A]
        	max(Qn(s, a))
        	
        	#computeActionFromQValues
        	max_a' Q(s', a')
        	
        	#getAction
        	if legal_actions:
            if flipCoin(1):
                action = random_choice
            else
                action = max_a' Q(s', a')(s)

        	
             estimate = r + gamma max_a' Q(s', a')
        
            #update
			alpha   <- policy(s)
			r       <- R(s,a)   # Receive reward			
			s'      <- T(s,a)   # Receive the new state
			Q(s',a) <- (1 - alpha) Q(s, a) + alpha(estimate)
			s       <- s'
			return Q
