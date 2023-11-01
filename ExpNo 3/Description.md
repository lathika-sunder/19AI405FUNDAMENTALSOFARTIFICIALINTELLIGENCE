<h1>ExpNo 3 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: Lathika Sunder</h3>
<h3>Register Number: 212221230054</h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>
A* Search Algorithm
1.  Initialize the open list
2.  Initialize the closed list
    put the starting node on the open 
    list (you can leave its f at zero)

3.  while the open list is not empty
    a) find the node with the least f on 
       the open list, call it "q"

    b) pop q off the open list
  
    c) generate q's 8 successors and set their 
       parents to q
   
    d) for each successor
        i) if successor is the goal, stop search
        
        ii) else, compute both g and h for successor
          successor.g = q.g + distance between 
                              successor and q
          successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)
          
          successor.f = successor.g + successor.h

        iii) if a node with the same position as 
            successor is in the OPEN list which has a 
           lower f than successor, skip this successor

        iV) if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)
  
    e) push q on the closed list
    end (while loop)
    
<h2>Program</h2>

```
from collections import defaultdict
H_dist ={}
def aStarAlgo(start_node, stop_node):
    open_set = set(start_node)
    closed_set = set()
    g = {}              
    parents = {}         
    g[start_node] = 0
    parents[start_node] = start_node
    while len(open_set) > 0:
        n = None
        #node with lowest f() is found
        for v in open_set:
            if n == None or g[v] + heuristic(v) < g[n] + heuristic(n):
                n = v
        if n == stop_node or Graph_nodes[n] == None:
            pass
        else:
            for (m, weight) in get_neighbors(n):
                if m not in open_set and m not in closed_set:
                    open_set.add(m)
                    parents[m] = n
                    g[m] = g[n] + weight
                else:
                    if g[m] > g[n] + weight:
                        #update g(m)
                        g[m] = g[n] + weight
                        #change parent of m to n
                        parents[m] = n
                        #if m in closed set,remove and add to open
                        if m in closed_set:
                            closed_set.remove(m)
                            open_set.add(m)
        if n == None:
            print('Path does not exist!')
            return None
        if n == stop_node:
            path = []
            while parents[n] != n:
                path.append(n)
                n = parents[n]
            path.append(start_node)
            path.reverse()
            print('Path found: {}'.format(path))
            return path
        open_set.remove(n)
        closed_set.add(n)
    print('Path does not exist!')
    return None
def get_neighbors(v):
    if v in Graph_nodes:
        return Graph_nodes[v]
    else:
        return None
def heuristic(n):
    return H_dist[n]
graph = defaultdict(list)
n,e = map(int,input().split())
for i in range(e):
    u,v,cost = map(str,input().split())
    t=(v,float(cost))
    graph[u].append(t)
    t1=(u,float(cost))
    graph[v].append(t1)
for i in range(n):
    node,h=map(str,input().split())
    H_dist[node]=float(h)
print(H_dist)
Graph_nodes=graph
print(graph)
aStarAlgo('S', 'G')

```
<h2> Graph I</h2>


![image](https://github.com/SaiDarshan2003/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/94692595/230b39db-f351-4abe-a4ad-cc1be52b3d09)


<h2>Input 1</h2>

![image](https://github.com/SaiDarshan2003/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/94692595/75add39b-e468-4acd-85c8-c8ac1db466ee)



<h2>Output 1</h2>

![image](https://github.com/SaiDarshan2003/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/94692595/ef4d5017-34d6-4c94-b59d-ea74c79b8250)


<h2>Graph II</h2>

![image](https://github.com/SaiDarshan2003/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/94692595/844d075c-1863-4018-b342-01c1135eb844)


<h2>Input 2</h2>

![image](https://github.com/SaiDarshan2003/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/94692595/a53e2ddb-ee13-4f58-9853-9c217f6e5402)


<h2>Output 2 </h2>

![image](https://github.com/SaiDarshan2003/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/94692595/7fc3cbdc-ed1c-459a-8195-6b3cb055b89a)


<h2>Result:</h2>
Thus,a Graph was constructed and implementation of A Star Search for the same graph was done successfully.
