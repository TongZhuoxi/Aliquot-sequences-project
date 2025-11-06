# Aliquot-sequences-project

def s(n):
    'function with input n, output is the sum of all divisors of n (except n)'
    
    #list of divisors
    divisors = []

    #checks every number up to n to see if they are divisors, and if they are, add to the divisors list
    for i in range(1, n//2 + 1):
        if (n % i) == 0:
            divisors.append(i)
            
    #returns the sum of all divisors of n, except for n itself.
    return sum(divisors)


def a(n, iterations):
    'function that gives the aliquot sequence of s(n). Inputs are n (the starting number), and iterations (number of elements in the sequence)'
    
    #the aliquot sequence of s(n) as a list, which is also the output.
    aliquot_seq = [n]

    for i in range(iterations - 1):
        
        #if s(n) = 0 then the sequence terminates.
        if s(n) == 0: 
            aliquot_seq.append(s(n))
            return aliquot_seq

        #if s(n) > 10^9 then the sequence terminates    
        elif s(n) > 10**9:
            return aliquot_seq

        #adds the current s(n) to the aliquot sequence and changes the input value to s(n)    
        else:
            aliquot_seq.append(s(n))
            n = s(n)    
            
    return aliquot_seq
