# 第一小時：Euler Paths & Cycles)

Hi everyone, welcome back. So as usual, we start with a recap. So last week we talked about graph theory. First we gave a basic definition of what an undirected graph is. Basically, a graph consists of two different sets, one is a set of vertices and the set of edges. The set of edges describes a relation among the vertices, basically every edge connects two vertices together. For an undirected graph, an edge from U to V is the same as an edge from V to U.

  

We talked about several different things about graphs. First thing we talked about is how to represent graphs so you can use the information more efficiently. So if you just want to describe a graph, list the set of vertices and list the set of edges is enough. But if you want to sort of get some information from the graph more efficiently, then you usually want to encode the graph in some more efficient methods. We talked about two different methods including a graph. First one is adjacency matrix, in which you can represent a graph with n nodes by an n by n matrix. And every index, every component of the matrix can represent whether there's an edge between two particular nodes U, V.

  

Next we talked about a very useful theorem, handshaking theorem. The theorem says, take a graph, take the sum of all vertex degrees, the sum of the degree must be equal to twice the number of edges. This is a very simple theorem, the proof is only a simple observation, but we are going to use this theorem over and over again in this class.

  

After that we start to talk about the important properties of a graph. So basically we define what the graph invariants are. Graph invariants are the values that remain unchanged under graph isomorphism. In other words, graph invariants are the values that remain unchanged when you, let's say, rename the vertices, draw the graphs differently, and so on. So these are the central properties of a graph. And in the next three weeks we are going to study different types of graph invariants. Last week we already talked about three graph invariants and their relationship. The first one is kappa of G, which is vertex connectivity. How many vertices do you need to remove in order to cut the graph into two disconnected pieces? The next one is lambda of G, edge connectivity. How many edges do you need to remove in order to cut the graph into two disconnected pieces? And the final one, delta of G. This is the minimum degree of the graph. And last week we proved a theorem which says that kappa of G is always less than or equal to lambda of G, which is less than or equal to delta of G.

  

Alright, so if not, today we are going to begin with one of the earliest problems studied in graph theory. This is called the Seven Bridges of Königsberg. Königsberg is a city in Europe and it's built on two sides of a river, and also in the river there are also several small islands. And the city also has parts on the islands. This city has seven bridges that go across these land pieces at these locations, roughly like this. These seven bridges are very well known and very beautiful, so for tourists to this city they would like to visit all seven bridges. So the question is, can you visit all seven bridges without repeat? Or, can you visit all seven bridges and go back to where you start without repeating any of the bridges?

  

This is the original question called the Seven Bridges of Königsberg. How is this related to graph theory? Well we can do a translation, translating this map into a graph. The city has four isolated pieces, for example you can call them A, B, C, D. In order to represent this problem as a graph theory problem, you can represent each of the land pieces as a node, as a vertex. So you have four nodes A, B, C, D. Whenever there's a bridge connecting two pieces of land, you draw an edge between them. So for example in between B and C there's a bridge, so in the corresponding graph you have an edge between them. Between A and C there are two different bridges, so you draw two different edges. And so on, so you can translate all the seven bridges into seven edges. Now instead of having a map with particular shapes and particular locations of the bridge, now I have a graph with four nodes and seven edges.

  

Now the original Seven Bridge problem translates to Graph Theory which asks this problem of, given this particular graph, can you find a path that goes through every edge exactly once? Or more generally, given an arbitrary graph, can you find a path that goes through every single edge of this graph exactly once? The problem was of course solved in 1735 by Euler. And therefore, the corresponding path that goes through every edge exactly once is called an Euler path or an Euler cycle. Let me formally define it. An Euler path or an Euler cycle of a graph is a path or cycle that goes through every single edge exactly once. Notice that this particular cycle can go through each node several times. That's okay. It doesn't have to be a simple cycle or a simple path. As long as it goes through every edge exactly once, no more and no less, it's an Euler cycle.

  

The first question of today is, given an arbitrary graph, we want to check whether this graph has an Euler cycle or not. Turns out that this is an easy question, you can check this property very easily. I'm going to directly tell you the answer. A theorem says a graph has an Euler cycle if and only if every vertex has even degree. This characterization is if and only if. So if a graph has an Euler cycle, if there's a cycle that goes through every edge exactly once, then every node, every vertex must have even degree. And on the other hand, if every node has even degree and the graph is connected, then there is an Euler cycle. Let me prove this theorem to you.

First, I'm going to show you that if a graph has an Euler cycle, then every vertex must have even degree. If a graph has an Euler cycle, then for every node I can look at how many times does the Euler cycle go through this particular node. Maybe the first time it goes in to this node and then goes out from another edge. And then if you keep following the cycle at some later point maybe it will again follow visit this node and then go out somewhere. And then another edge goes in, another edge goes out, and so on. And suppose this happens k times. So suppose the Euler cycle actually visit this particular node k times. It means that it goes into this node k times, goes out of this node k times. But we know that the Euler path, Euler cycle actually only visit every single edge exactly once. So every single one of this edge must be different. And every edge is visited, so every edge connecting to this node must be visited on this cycle. So I already listed every single one of the edges connecting to this node exactly once, so suppose this node is V, then the degree of V must be exactly 2k, which is an even number. The idea is that if the Euler cycle goes through the node exactly k times, then the degree of this node must be exactly 2k. k edges going in, k edges going out. And therefore every degree is even.

(Student question: Does the Euler cycle need to go back to the same point?) Very good. So the question is, does the Euler cycle need to go back to the original starting point after visiting all the edges? And the answer is yes, because it's a cycle, it must have the same starting and ending point. And so, besides the middle node which the cycle can go through k times, you actually have a beginning node which the cycle starts from. The cycle might start from this node, and then in the middle might go through it a couple of times. But at the end, it must end at the same beginning node, so there's one last edge that goes back to this beginning node. So if you check the beginning node, where you have one edge going out at the beginning, it must have one final edge coming in at the very end.

Next we are going to show the reverse. If a graph have all degrees being even, then it must have an Euler cycle. Instead of giving you a formal proof, I'm going to show you an example. This example has all degrees being even. I'm going to show you step by step how to construct an Euler cycle out of this graph. Step one, I'm going to find a random cycle in the following way. I'm going to pick a random starting point, let's say this one. Follow an arbitrary edge and start moving forward. Whenever I reach a new node, if there are some other edges going out, I keep following the edges. If there are multiple edges that are going out, I choose an arbitrary one and keep following. There's another edge going in, I keep following. There's another edge following. There are multiple choices, I choose an arbitrary one, let's say pick this one, keep following. Now at this point there are no more edges that I can follow. And therefore I stop right here.

First of all I want to show you that whenever this process ends, I always get a cycle. I always stop in my starting point. Why is this true? Well, whenever I reach a new node, this new node originally it has even degree. Now I use one of its edges to go into that node, so when I occupy this edge, the new node has the degree decreased by one. So originally the new node has even degree. Now when the degree decrease by one, whenever I reach this new node, the degree decrease by one and therefore the node has odd degree. By odd degree it means that the degree of the new node is not zero. And therefore I always have another edge going out. So whenever I reach a new node, the degree of this new node becomes odd because there's one edge I used for coming in. And therefore there is always at least one edge that I can use to go out. So when can I stop? The only location that I can stop this process is when I reach the original starting point. Because when I start, I used one degree of the starting node. And therefore the starting node now has odd degree, and so whenever I go back to it I have a chance to stop.

  

Now again, ignoring the yellow cycle, ignoring the blue cycle, the remaining of the graph must still have all degrees being even. Because, similar to the example in the previous part, whenever I take a cycle and remove a cycle, the effect on the degree of every node is even. I'm reducing the degree of every node by an even number. So just by removing these cycles, the remaining graph still have all degrees being even. So I can repeat this process. Find one cycle after another after another, until the graph is decomposed into many different cycles. Instead of one single cycle that goes through every edge exactly once, I have several cycles that all combined together visit every edge exactly once. This is step one. Find some cycles that visit each edge exactly once.

Now the final task here is to combine several cycles into one single cycle. If I can find a method to combine different cycles into one single cycle, then I can combine all of these cycles gradually into an Euler cycle. How do I do this combination? Well, let's assume that I want to combine this yellow cycle and the red cycle. What I do is starting from the yellow cycle, I follow the edges until I see the red cycle for the very first time. When I first see the red cycle, I start following the red cycle all the way around until I go back to this point. And then after coming back, I follow the rest of the yellow cycle. In this way now I get a new cycle which goes through every single edge on the red cycle and the yellow cycle exactly once. Each time I can take two cycles with at least one intersecting point and combine these two cycles into a single one. Step two, combine pairs of cycles into a single cycle. I can keep repeating this process... and eventually I will be able to combine every single cycle on this graph into a large single cycle, which is the Euler cycle that we are looking for.

(Student question: Is it possible that there is no common node that connects two different cycles...) Very good. The question is, is it possible that after some rounds of combinations I'm now ending with several cycles, but if you look at any pair of cycles there are no intersecting points, so I cannot combine them. Well the trick is that the graph is connected. So if I can split the graph into several cycles and none of them intersect each other, then the graph is split into several pieces that are not connected to each other. Because if these cycles do not have intersecting points, then they are not connected to each other. So if the whole graph is combined together and you have a bunch of cycles, at least two of the cycles must have an intersecting point, and so you can keep combining the cycles. This is where the connected condition comes in.

Now we introduce the first notion which is an Euler path or an Euler cycle, which is a path or cycle that go through every edge exactly once. Given a graph it's very easy to test whether an Euler cycle or an Euler path exist. Just count the degree and check whether the graph is connected and that's it. There is a different notion which talks about a cycle or a path that goes through every vertex exactly once. And that's called a Hamiltonian cycle or a Hamiltonian path. In this new, different definition, a Hamiltonian path or a Hamiltonian cycle does not have to go through every edge. All you need is to go through every node exactly once.

It's named after Hamilton. Turns out that Hamilton is actually not the first person who studied Hamiltonian cycle. Hamilton did two things. First he made some connection to graph theory and tried to study general cases, general in his base is like general polyhedrons... He also during the process invented a board game called Icosian game. This is a board game, and the content of the game is essentially they give you a graph and your goal is to find a Hamiltonian cycle on this graph. As you might have expected, this game didn't sell very well, but during his study more people know about Hamiltonian cycles and their properties, and so we named this type of cycle Hamiltonian cycles.

It turns out that unlike deciding whether a graph has Euler path or Euler cycle, which is an easy problem, given a graph deciding whether there exist a Hamiltonian cycle or not is actually a difficult problem. It's actually NP-complete, if you know what it is. So given a graph deciding whether there exist Hamiltonian cycles is actually computationally difficult. So instead of giving you some simple theorem that directly allows you to test whether a graph has Hamiltonian cycles, I'm going to give you some conditions.

Let me begin with one type, one class of graph that never has Hamiltonian cycles. The theorem says any bipartite graph with an odd number of vertices does not have Hamiltonian cycles. There's a new term here, bipartite graph, which I haven't defined. Bipartite graphs are graphs where you can split the nodes into two sets, A and B. And every edge connects one node in A to one node in B. So you can have all these edges in between. This is a bipartite graph. This type of graph is actually very widely used in different scenarios. For example in matching. So for example you are matching courses to classrooms... Also I'm going to introduce another smaller set called complete bipartite graph. A complete bipartite graph is a graph with m nodes on one side, n nodes on the other, and between every pair of nodes from left to right there's an edge in between. For example this particular graph is called K4,3. In general we can define complete bipartite graph K m,n which is a special case of bipartite graphs.

# 2nd hour - Hamiltonian path/cycle and example of planar graph

Um, in the first hour of this class, we provided a condition such that, um, satisfying this condition guarantees that the graph does not have a Hamiltonian cycle. Um, more precisely, we show that any bipartite graph with odd number of vertices does not have a Hamiltonian cycle. So, um, if anything of, um, the second hour, I'm going to give you a condition such that, um, if a graph satisfies this condition, it is guaranteed to have at least one Hamiltonian cycle. Okay, um, they may not know where the Hamiltonian cycle is, but it is guaranteed to exist.

  

Okay, um, instead of giving you one theorem, I'm actually going to give you two different theorems. So the first is direct theorem. Direct theorem says that, um, given any graph with n nodes, if every node has degree at least n over two, then it has a Hamiltonian cycle. Okay, um, you need at least two nodes, um, you can easily check that two nodes, um, with degree one, um, doesn't satisfy the condition. But, um, even if you are given a node, uh, sorry, if you are given a graph with n different vertices, and every single one of these vertex has degree at least n over two, then the graph must have a Hamiltonian cycle.

  

Okay, notice that, um, in this particular theorem, I don't even have to say the graph is connected. Okay, the number of degrees is large enough such that the connectivity of the graph is already guaranteed by the degree. Okay, if every, if every node has degree at least n over two, the graph must be connected. There's no way you can cut it. So, um, recall that last week I talked about another theorem proved by, um, Dirac, and, um, here we see the direct theorem, which is more famous than the theorem I talked about last week. And so this is the direct theorem.

  

Instead of proving direct theorem, I'm going to prove a stronger theorem called Ore's theorem. Ore's theorem says instead of requiring every node to have high degree, instead of requiring every node to have degree at least n over two, all I need to have is an n-vertex graph such that every two nodes has total degree at least n. This is already enough to guarantee that there is a Hamiltonian cycle. Okay, notice that if every node has, um, degree at least n over two, then, um, the degree of any two nodes must sum up to at least n. So, um, if you satisfy the condition for direct theorem, you directly satisfy the condition for Ore's theorem, and therefore you have a Hamiltonian cycle.

  

Okay, so, um, before I prove Ore's theorem, is there any question about the statement of the theorem? These graphs are simple. Okay, they cannot have multiple edges or loops. Okay, um, for, for general graphs, um, you can always remove multiple edges and loops and do these steps. Because, um, multiple edges and loops never helps in, in finding Hamiltonian cycles, so I'm not going to care.

  

Okay, thank you. Any other questions? Alright, so let's prove, um, Ore's theorem. I'm going to prove by contradiction. Suppose that in the original graph G, this is original graph, I already have, um, for every pair of node UV, degree of U plus degree of V greater or equal to n for every pair of nodes UV. But this particular graph G does not have Hamiltonian cycle.

  

Suppose I have a graph like this. What I can do is I can add a random edge to G. Add another random edge to G, so I can keep adding edges until at an endpoint where I have a graph G prime, add one more edge, I get a G double prime, where G prime still has no Hamiltonian cycle. But after adding one more edge, I suddenly have the Hamiltonian cycle. Okay, the transition always exists because, um, given any graph G, when you keep adding one edge after another, eventually you're going to get a graph with Hamiltonian cycle. In the worst case I'm going to add an edge between every pair of nodes and get a complete graph and there's a Hamiltonian cycle in this.

  

Okay, so I just add random edges to G arbitrarily. And at some point there must be a transition where after I add one more edge, it suddenly, the graph suddenly goes from no Hamiltonian cycle to a new graph that has a Hamiltonian cycle. Okay, so I must be able to find a transition between G prime and G double prime such that they only differ by one edge. But G prime does not have Hamiltonian cycle, G double prime do have a Hamiltonian cycle. The transition always exists, and I'm going to find a contradiction right here.

  

Okay, so what kind of property does the graph G prime and G double prime have? Notice that G double prime now has a Hamiltonian cycle. Meaning that there's a single cycle that goes through every, uh, sorry, that goes through every vertex exactly once. If I look at the final edge being added from G prime to G double prime, it must be on this cycle. Right, otherwise this cycle already is already in G prime and so G prime has a Hamiltonian cycle, which is not true. So the final edge being added must be somewhere on this cycle.

  

So before I add this one final blue edge, if I look at the remaining of this Hamiltonian cycle, it is now a path that goes through every edge exactly, sorry, that goes through every vertex exactly once. So this particular graph G prime has a Hamiltonian path, but do not have a Hamiltonian cycle. Okay, so right now I can find a graph G prime that has a Hamiltonian path, but there are no Hamiltonian cycle. And also G prime is obtained by add more edges to G. And therefore the degree of every node in G prime is larger is greater or equal to the degree of every corresponding node in the original graph. So this new graph G prime also satisfies the condition that, um, adding the sum of the degree of any two nodes UV must be at least n.

  

In particular, the beginning and the ending node of this Hamiltonian path must have degree at least n. Okay, so let me repeat this process. This is, um, probably the most difficult step for you to understand this proof. So given, I want to prove by contradiction, given a graph with very high state with very high degree, but no Hamiltonian cycle, I want to derive a contradiction. The contradiction does not happen directly on this graph, but instead, what I can do is I'm going to keep adding more and more edges to the original graph until at some point when I add one more edge, I suddenly go from no Hamiltonian cycle to a graph that has a Hamiltonian cycle.

  

So right before I add the final blue edge, I have this very special graph G prime. G prime has a Hamiltonian path but does not have a Hamiltonian cycle. But again G prime is obtained by adding edges from G, so G prime also satisfies this high degree condition. I'm going to show you that just looking at G prime, this graph by itself with all these conditions, I can derive a contradiction. Okay, so now I'm going to say everything else is not important. I'm going to remove all the information about everything else. I'm going to say that suppose you give me any graph G prime that has a Hamiltonian path but no Hamiltonian cycle, and has very high degree, meaning that adding these two end points of the path has total degree at least n, this is impossible. I'm going to show it here. I'm going to show you that these type of graph G prime does not exist.

  

I'm going to show that this type of graph G prime does not exist by proving that if G prime has a Hamiltonian path and has high degree, then it must have a Hamiltonian cycle. Okay, so I'm going to start with a graph G prime, it has a Hamiltonian path, it has high degree, and I'm going to prove to you that G prime has a Hamiltonian cycle. And therefore it reaches a contradiction.

  

Okay, so before I talk about the structure of G prime and derive this contradiction, any question about, um, the proof structure? Alright, now in the very end I need to talk about the structure of the graph G prime. Okay, so G prime has a Hamiltonian path from U to V. So I can draw a path from U to V that goes through every node exactly once. So every node of G prime is now on this path. Okay, I know that UV must have high degree. Degree U plus degree V must be greater or equal to n. So the starting and ending node must have total degree at least n.

  

Since every single node is on the path, the edges of U must be connecting to different nodes on this path. Similarly, if I look at the edges of V, it must also connect back to this path. Okay, so maybe the edges of V connects right here, at these nodes. Okay, so given that G prime has a Hamiltonian path and has a high degree on its beginning and ending notes, I'm going to look at this part. I'm going to look at this path and I'm going to make two different marks.

  

Okay, so I'm going to make some marks by, um, for every node in the neighborhood of U, for every node that U links to, I'm making an X mark to the left of this node. What do I mean? So U connects to this node, so I mark an X to its left. U connects here, I mark an X to its left. U connects here, I mark an X to its left. U connects here, I mark an X to its left. U connects here, I mark an X to its left. U connects to here, so I mark an X to its left. So now this is the first type of marks that I did. So whenever U connects to a certain node, I mark an X to its left.

  

Next, for every node connecting to V in the neighborhood of V, for every node that V connects to, I'm going to directly circle it. So V connects to this node, I'm going to circle it. V connects to this node, I'm going to circle it. V connects to this node, I'm going to circle it. Okay, so I'm going to make some marks throughout this Hamiltonian path. Okay, so any question about how I make this marks?

  

Okay, so I want to make some observations. First, I have at least n marks. Because the number of X I marked is equal to degree of U. The number of circles I marked is equal to degree of V. So since degree of U plus degree of V greater or equal to n, I made at least n marks. Furthermore, V is not marked. Because V does not connect to itself, so all the circles are on the other nodes. For the node V, so for the node U, whenever U is connected to a certain node, we mark some node to its left. So we never mark V. Regardless of which mark we are using, V is never marked.

  

So we only have the total of n nodes, only n-1 of them can receive marks. So as a result, there must be at least one node receiving both marks. Okay, there must be since I'm making at least n marks in n-1 nodes. There must be this one node receiving both marks. Maybe multiple nodes, but at least one node receiving both marks.

  

What happens here? It receives a yellow mark and therefore there's an edge from U to its right. This is the definition of the yellow mark. It receives a blue mark, so there's an edge from V to this node. There's a path here. There's a path here. The red path forms a Hamiltonian cycle. So whenever two marks overlap, I can find the red Hamiltonian cycle. It always exists.

  

So given that a graph has a Hamiltonian path, and the two end points of the Hamiltonian path have total degree at least n, the graph also has a Hamiltonian cycle. Which is a contradiction, because we start by saying there's a graph with only Hamiltonian path and high degree but no Hamiltonian cycle. And this cannot happen. So we derive a contradiction, and the only possibility is that our initial assumption is wrong. Which says, um, our initial condition says, um, a graph may have high degree and no Hamiltonian cycle, and this must be wrong. So, therefore, um, we prove this theorem.

  

Okay, so look at the overall structure again. If we had a graph G that has high degree but no Hamiltonian cycle, we can keep adding more and more edges until we have an edge, we have a new graph G prime, which only has Hamiltonian cycle but no Hamiltonian, uh, sorry, only have Hamiltonian path but no Hamiltonian cycle, but at the same time having high degrees. And this is not possible. Alright, so any question about, um, the proof of Ore's theorem?

  

Alright, um, if not, I'm going to quickly mention two more conditions that guarantees the existence of Hamiltonian cycles. Um, for these two theorems I'm just going to mention it without proving it. Um, but these two theorems sort of makes a connection between the current topic, Hamiltonian path, and the next topic I'm going to talk about, which is planar graphs. So, um, let's look at the following two theorems. Okay, so, um, this is a theorem by Tutte in 1956. The theorem says any 4-connected planar graph has a Hamiltonian cycle.

  

So let me explain what these two terms means. 4-connected means kappa is at least 4. Okay, so you need to cut at least 4 vertices to cut it into two disconnected pieces. So whenever you see k-connected, it means that kappa is at least k. So 4-connected means that, um, the connectivity is at least 4, you need to cut at least 4 vertices to cut it apart. And it has to be, um, planar, which I define a little bit later, but, um, basically planar means that you can draw the graph on a plane without edge crossings. Okay, so suppose a graph is 4-connected and it can be drawn on a plane without edge crossings, then it must have a Hamiltonian cycle. This is another condition that guarantees the existence of a Hamiltonian cycle. And in fact, the theorem can be strengthened.

  

Okay, there's a stronger theorem by Thomassen in 1983, which says given a graph G which is 4-connected and can be drawn on a plane. Given any two notes in G, so you pick any starting and ending point in G. I can find a Hamiltonian path starting from U and ending in V. So I can start from any given note U, pick any ending note V, I can start from U, visit every note exactly once, and end at V. And this holds for every pair of notes UV. So if you give me different pairs of notes, I can give you different Hamiltonian paths. So this graph is so well connected that given any starting point, given any ending point, there is a Hamiltonian path in between.

  

Okay, so for these theorems, um, you can see that, um, different properties, different graph invariants such as connectivity, um, planarity, and also the existence of Hamiltonian cycle can be related to each other. Okay, um, the proof of these two theorems are, um, out of scope for, um, this class, but, um, if anyone is interested, I already give the name and date so you should be able to find the proof of this theorem pretty easily online. Alright, so, um, these two theorems are just, um, supplementary. They are not going to be used in any homeworks or exams. Okay, so you don't need to remember this theorem or use these two theorems in any way.

  

Um, alright, so this is the end for, um, the topic related to Hamiltonian paths, Hamiltonian cycles. Basically, um, checking whether a graph has a Hamiltonian path or Hamiltonian cycle is a difficult problem. So I give some conditions where, um, for example if it's bipartite and has an odd number of vertices, then it never has a Hamiltonian cycle. Some other conditions like, all nodes have high degree, then it always has a Hamiltonian cycle. Or there are some connect connection between um, 4-connected plus planar, then it always has a Hamiltonian cycle. Okay, so you can have a lot of, um, characterization theorems like this, so that given a certain condition, you can guarantee that it always has a Hamiltonian cycle or never has a Hamiltonian cycle.

  

Alright, so, um, for the last 15 minutes of today's class, I would like to very briefly introduce a new notion called, um, planar graphs. I would like to formally define what a planar graph is, and give you some examples of what is a planar graph, what is not a planar graph. Okay, I'm going to spend a whole week next week talking about planar graphs, properties that a planar graph may have. So, um, this is a longer chapter, um, so, um, I'm going to start early today by just giving you the definition.

  

Okay, so the definition is, a graph is planar if it can be drawn in a plane without edge crossings. Okay, if there's at least one way to draw it in a plane without edge crossing, then it's a planar graph. Let me give you an example of a planar graph. Okay, so, first example. This particular graph, K4, is a planar graph. Well, you may notice that in this particular drawing, there are two edges crossing each other. So this is not a planar drawing. But you can draw it differently. For example, you can draw it like this, moving one of the diagonals outside, and it becomes a planar graph. So at least, um, if you can find one such drawing, then the whole graph is planar.

  

Okay, of course you can find a lot of other drawings where you have edges crossing each other. You can draw these edges pretty arbitrarily. But, um, and you may find a lot of different drawings such that the edges are not crossing each other. For example, um, this is a different drawing of the same graph. And it still does not have edge crossings. Okay, so proving that a graph is planar is easy. All you need to do is find one drawing that, um, does not have edge crossings. So proving a graph is not planar is much harder, because you have to show that every drawing must have edge crossings.

  

So I'm going to show you one such example. Okay, the example is K3,3. A complete bipartite graph with 3 nodes on each side. So, um, basically I have 3 nodes to the left, 3 nodes to the right. Every node on the left and every node on the right has an edge connecting between them. So there are 9 edges total. Okay, I'm going to show you that this particular graph does not have a planar drawing. Again, whenever you draw this on a plane, it must have edge crossings.

  

Alright, I'm going to do it in the following. So first I'm going to look at these 4 nodes, 1, 2, 3, and 4. For these 4 nodes, 1 is connected to 2, 2 is connected to 3, 3 is connected to 4, and 4 is connected to 1. Okay, so if you draw these 4 different nodes on the plane without edge crossings, you must have node 1, node 2, node 3, node 4. Okay, so you can draw it pretty arbitrarily. You can put the node anywhere, you can bend the edges and so on, but they must surround a region. Okay, these 4 nodes, 1, 2, 3, 4, and these 4 edges must surround a region.

  

I'm going to look at the next node, node 5, and see where it is. Okay, so node 5 has connections to nodes 2 and 4. There are two possibilities. 5 is either inside the region or outside the region. Okay, so, um, let's only look at the case where it's inside the region. The case where it's outside is symmetric, you can do it at home. But when it's inside the region, since it has an edge to node 2, it has an edge to node 4, these two edges is going to cut this region into two parts. Okay, so node 5 is in the middle of the region, this region will be cut into two pieces, and there's an outer region, and now we can discuss where node 6 is.

  

Well, if node 6 is right here, since, um, 6 has an edge connecting to node 3. Node 6, in order to connect to node 3, it must have edge crossings. So node 6 cannot belong to this region without edge crossings. How about this region? Well, node 6 has an edge to node 1. So if it's right here, in order to connect node to node 1, it must create an edge crossing. So you cannot draw node 6 right here without an edge crossing. How about the outside? Well, now node 6 has an edge to node 5. If you draw it outside, in order to connect 5 and 6, you must create an edge crossing. So without edge crossing you also cannot draw node 6 right here.

  

So there's nowhere you can put node 6 without edge crossings. So in this way, regardless of where you put node number 6, you always introduce an edge crossing. Okay, so this is the case where 5 is in the middle of this region. There's another case where 5 is outside of this region, um, you can also discuss the cases and prove that, um, node 6 also always create a cross. Okay, so just by discussing all possible cases, you can show that regardless of how you draw this graph K3,3, you always have an edge crossing, and therefore K3,3 is not a planar graph.

  

Okay, so any questions about these two examples? K4 is a planar graph, K3,3 is not a planar graph. (Question from student: How is this planar graph connected to our daily life?) Okay, so, um, how is planar graph connected to our daily life? Okay, there are many different, um, ways that planar graphs might be connected to our daily lives. For example, um, we may want to run some of the algorithms only on planar graphs. For example, shortest path algorithms. Because we want to find shortest routes on a map, which is planar. For example, um, if we have a circuit, which can be sort of represented by, um, if you represent each element, each, um, circuit element by a node, each wire by a line, by an edge, then a circuit belongs to a graph. And you might want to draw a circuit on a plane, because you can put it on a circuit board. Okay, so there are many different uses of planar graphs in daily lives. So, um, you might want to draw a graph on a plane, or you might want to run some certain algorithms only on planar graphs. These are, um, common applications of planar graphs. And so if you know some of the properties for planar graphs, it may help you in these kind of problems.


Alright, I would like to give you one last example without proof. K5, five nodes fully connected complete graph. This is not a planar graph. You can also prove that it is not planar by...