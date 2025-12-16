---
title: "Counting Incomplete 3D Connected Cubes"
date: 2025-11-30
tags: [math, geometry]
---

{% include mathjax.html %}

From my office I saw this problem, which is based on a 3Blue1Brown video, posted on a colleague's desk:

> Consider the set of all **incomplete, open cubes** that are also  
> **3-dimensional**, **connected**, and **rotationally unique**.  
> What is the size of this set?
>
> **Definitions**
>
> • **Open Cube:** Only the edges are present; no faces exist.  
> • **3-D:** The structure must include at least one edge oriented along each of the three coordinate axes.  
> • **Connected:** The structure is a single contiguous graph (no separate components).  
> • **Rotationally Unique:** Two structures are considered the same if one can be rotated to match the other.

I decided to take a jab at this problem in my free time. And after a couple of months, I was able to solve it. In this post, I'll share my solution and thought process.

**Disclaimer:** I tried to limit my use of computers for this problem, but I did use it to solve a portion of it.

## Initial Thoughts

Immediately when I read the problem, I thought it had to be related to Burnside's Lemma, which is a counting technique often used to solve problems involving symmetry.

The formula for Burnside's Lemma is:

$$ |X/G| = \frac{1}{|G|} \sum_{g \in G} |X^g| $$

If you haven't taken Abstract Algebra, this formula may look pretty daunting. You also need to understand group actions. I won't go into all the details, but I'll try to explain everything in layman terms. I am also going to handdraw the pictures in this article so apologize if they look bad :P.

## Understanding the Problem

Let's first define what it means to do an "action" on a cube. Because this is a fixed cube (rigid body), the only actions I can do are rotations. There are 24 possible rotations for a cube:

1. Identity rotation AKA not doing anything (1 way)
2. 90-degree and 270-degree rotations about axes through centers of faces (6 ways)
3. 180-degree rotations about axes through centers of faces (3 ways)
4. 60-degree and 120-degree rotations about axes through opposite vertices (8 ways)
5. 180-degree rotations about axes through midpoints of opposite edges (6 ways)

I recommend looking at this link visaulizing all the rotations. It will be helpful for understanding the solution below: [Cube Rotations](https://www.euclideanspace.com/maths/discrete/groups/categorise/finite/cube/index.htm)

Now lets look at some incomplete-3D-connected cubes (i3c) and their orientations. I'll define an orientation as the position of the cube after a rotation. For example, lets look at this i3c cube:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/missing_leg_table_cube.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    An i3c cube resembling a table with a missing leg. The dashed line indicates the absent edge.
  </figcaption>
</figure>

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/missing_leg_table_cube_transform.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    After rotation, the missing leg shifts to the left. I colored the faces blue to help visualize the axis of rotation.
  </figcaption>
</figure>

Although these are the same cubes, they are in different orientations. How many possible orientations are there for this cube specifically?

Well, suppose the "tabletop" is on the top, the missing leg can be on any four. So I have four orientations there. But now change the position of the tabletop: the tabletop can be on any of the six sides. So in total, there are 4 * 6 = 24 orientations. It may seem like a coincidence that for this i3c cube there are 24 different orientations and for a cube in general there are 24 different possible rotations. In turns out that if you apply the all possible rotations on this i3c cube (you can define the starting orientation as anything), you can get all possible orientations for this cube!

But does this apply to all cubes? No. Let's look at this i3c cube:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/complete_table_cube.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    This i3c cube resembles a complete table.
  </figcaption>
</figure>

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/complete_table_cube_transform.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    After face rotation, the orientation remains unchanged.
  </figcaption>
</figure>

So if I want to count all possible orientations for this complete table, its just counting the number of faces on a cube, which is six. This is because I can put the tabletop on any of the six sides. Obviously, this is less than the number of rotations of a cube, which is 24, because some rotations will lead to the same orientation, as shown in the picture.

But why should I care about symmetries of various cubes? How does it relate to the problem? It turns out that counting symmetries is the key to understanding how many unique i3c-cubes there are! So lets describe the notation used in Burnside's Lemma, and then I can finally apply it for the solution.

### Notation

$$ |X/G| = \frac{1}{|G|} \sum_{g \in G} |X^g| $$

$$
X = \text{Set of all orientations of all possible i3c-cubes.}
$$

$$
G = \text{Set (group) of all rotations of a cube.}
$$

$$
|X/G| = \text{number of unique i3c-cubes (what I want to find)}
$$

$$
|G| = \text{Number of rotations of a cube which is 24.}
$$

The next one is the important one:

$$
\sum_{g \in G} |X^g|
$$

For each rotation $$ g \in G $$, I count the number of orientations that remain unchanged after applying $$ g $$. And at the end, I sum them all up and finally divide by 24. This is basically the crux of the problem.

## Solution

Instead of going through all of the 24 rotations one-by-one, I can simplify the counting by grouping similar rotations together. I actually already did that when I listed the five families above in the page. So now, I just need to look at one rotation from each family, see how many orientations remain unchanged, and then multiply by the number of rotations in that family.

Note: I will do the identity "rotation" last, as that ironically is the hardest one to count.

### 90-degree and 270-degree rotations about axes through centers of faces (6 ways)

For this rotation, I'm going to have the axis of rotation going through the centers of the top and bottom faces. This rotation is pretty restrictive for symmetries. There are only two orientations that remain unchanged after applying this rotation:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/90_face_rotation.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    After a 90 degree face rotation, the orientation remains unchanged.
  </figcaption>
</figure>

Now since there are six rotations in the family, the total count here is: $$ 2 * 6 = 12. $$

### 180-degree rotations about axes through centers of faces (3 ways)

Similar to above, I'm going to have axis of rotation going through the centers of the top and bottom faces. This rotation is less restrictive than those in the previous family, so there will be more orientations here. For this, I basically brute forced all possible orientations.

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/180_face_rotatation_enumeration.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    I enumerated 22 cubes that remain unchanged after applying this rotation.
  </figcaption>
</figure>

The total count here is: $$ 22 * 3 = 66. $$

### 60-degree and 120-degree rotations about axes through opposite vertices (8 ways)

This is one's a bit tricky to visualize. But from a certain vantage point, this is also a pretty restrictive rotation. If you look at the cube directly from the axis of rotation through a pair of oppsite vertices, you can see the cube looks like a hexagon. And the rotation is basically rotating this hexagon by 60 or 120 degrees.

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/edge_rotation_shape.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    The shape is a hexagon through this vantage point.
  </figcaption>
</figure>

I can start off by finding all the symmetries for this 2-D hexagon shape. Okay, but then what? I still need to enumerate all the corresponding i3c cubes.

To find the cubes using this method, I realized that these shapes only describe the vantage point looking directly at one vertex. I need to pair this view with another view from the opposite vertex to get a completed i3c cube. Note that compatible pairs must share the same edges on the ring of the hexagon. Here are all the possible symmetries for this hexagon shape:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/edge_rotation_vantage_points.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    The edges between two symmetries indicates that they are compatible.
  </figcaption>
</figure>

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/edge_rotation_example.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    An example pair of symmetries that make a i3c cube.
  </figcaption>
</figure>

So after looking at all compatible pairs, I can enumerate all possible orientations that is symmetrical through a vertex rotation:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/edge_rotation_enumeration.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    I enumerated 11 cubes.
  </figcaption>
</figure>

The total count here is: $$ 11 * 8 = 88. $$
### 180-degree rotations about axes through midpoints of opposite edges (6 ways)

Now this is probably the trickiest one to visualize, and this is also the non-identity family that contains the most symmetries so I can't enumerate them all into a picture. But I can still find the total count using the same vantage point technique as above. If you look at the cube from the axis of rotation through the midpoints of opposite edges, you get this shape:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/third_part_shape.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    The shape is similar to the Equinix logo.
  </figcaption>
</figure>

In order for this method to work, I realized compatible pairs of this shape must share the left and right edges circled in the picture above.

So I can split this section into two cases:
- **Case 1:** The shape contains both the left and right edges (hard lines).
- **Case 2:** The shape does NOT contain both the left and right edges (dashed lines).

#### Case 1:

Here are the possible symmetries:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/case_1_symmetries.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    There are seven symmetries for this case.
  </figcaption>
</figure>

Note that the ones on the first row cannot be i3c cubes alone and are incompatible with each other. However, the ones on the second row can be i3c cubes alone, and are compatible with all of the symmetries, including those on the first row.

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/case_1_example.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    An example i3c cube made from two compatible symmetries from the first and second rows
  </figcaption>
</figure>

To find the count:

- Looking at the second row first: The four symmetries can all be paired with each other, including itself. Note that the order matters as well. I am also subtracting one to remove the complete cube. So the count from the second row is: $$ 4 * 4 - 1 = 15 $$.
- Now looking at the first row: each of the three symmetries can be paired with any of the four from the second row. I am multiplying by two because order matters. So the count from the first row is: $$ 3 * 4 * 2 = 24 $$.

So in total for case 1, the count is: $$ 15 + 24 = 39 $$.

#### Case 2:

Here are the possible symmetries:

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/case_2_soft_lines.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    There are also seven symmetries for this case. *Ignore the soft edges*.
  </figcaption>
</figure>

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/case_2_example.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    And here is an example of a compatible pair that makes a i3c cube.
  </figcaption>
</figure>

Now from here, I basically had to eyeball all the compatible pairs.

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/case_2_hard_lines.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    I drew 14 edges between compatible pairs.
  </figcaption>
</figure>

Each edge between two symmetries indicates that they are compatible. And they're all bidirectional edges (except for the one that loops into itself), so each edge indicates two compatible pairs. So from counting all the edges, I get a total of 13 bidirectional edges and one self-loop. So the total count for case 2 is: $$ 13 * 2 + 1 = 27. $$

So from these two cases, the total count for this family is: $$ (39 + 27) * 6 = 396. $$

### Identity rotation (1 way)

Now is the time for the identity rotation. This one is "interesting" because the identity rotation keeps all orientations unchanged. So basically, I need to count all possible orientations for all i3c cubes. I couldn't figure out a way to do this through combinatorics, so I wrote a program instead to count it.

#### Implementation for finding all incomplete 3D connected cubes and orientations.

The following is the code where I used DFS to find all of the orientations. The adjacency matrix represents the edges of the cube and it's connections.

<figure style="text-align:center">
  <img src="/assets/images/i3c_cubes/adjacency_matrix.png" alt="i3c cube with one missing edge" width="320">
  <figcaption>
    The illustration of the adjacency matrix that I used in the code.
  </figcaption>
</figure>

```python

def incomplete_3d_connected_cube_count():
    # used to check if cude is 3d
    is_x_visited = [False]
    is_y_visited = [False]
    is_z_visited = [False]

    all_incomplete_cubes = set()
    visited = set()

    # the adjacency matrix of the cube based on the picture above
    adj_matrix = {"x1": ["z1", "z2", "y3", "y4"],
                  "x2": ["z1", "z2", "y1", "y2"],
                  "x3": ["z3", "z4", "y3", "y4"],
                  "x4": ["z3", "z4", "y1", "y2"],
                  "y1": ["x2", "x4", "z1", "z4"],
                  "y2": ["x2", "x4", "z2", "z3"],
                  "y3": ["x1", "x3", "z1", "z4"],
                  "y4": ["x1", "x3", "z2", "z3"],
                  "z1": ["x1", "x2", "y1", "y3"],
                  "z2": ["x1", "x2", "y2", "y4"],
                  "z3": ["x3", "x4", "y2", "y4"],
                  "z4": ["x3", "x4", "y1", "y3"]}
    
    # This DFS is basically brute forcing all possible connected cubes
    def dfs(node):
        if node in visited:
            return
        visited.add(node)
        if node.startswith('x'):
            is_x_visited[0] = True
        if node.startswith('y'):
            is_y_visited[0] = True
        if node.startswith('z'):
            is_z_visited[0] = True

        if is_x_visited[0] and is_y_visited[0] and is_z_visited[0]:
            all_incomplete_cubes.add(frozenset(visited))

        adj_set = set()
        for n in visited:
            for neighbor in adj_matrix[n]:
                if neighbor not in visited:
                    adj_set.add(neighbor)
        
        for neighbor in adj_set:
            dfs(neighbor)
        
        visited.remove(node)
        # now check if all visited contains x,y,z
        is_x_visited[0] = False
        is_y_visited[0] = False 
        is_z_visited[0] = False
        for v_node in visited:
            if v_node.startswith('x'):
                is_x_visited[0] = True
            if v_node.startswith('y'):
                is_y_visited[0] = True
            if v_node.startswith('z'):
                is_z_visited[0] = True

    # start DFS from each node
    for start_node in adj_matrix.keys():
        dfs(start_node)

    return len(all_incomplete_cubes) - 1 #removing complete cube

```

This code takes about five minutes to run, and at the end it returns 2366.

### Final Calculation

I have all of the counts for each family of rotations. Now I can plug everything into Burnside's Lemma:

$$
|X/G| = \frac{1}{24} (12 + 66 + 88 + 396 + 2366) = \frac{2928}{24} = 122
$$

So the final answer is: **122 unique incomplete 3D connected cubes**.

---
## References
- [3Blue1Brown Video on the cubes](https://www.youtube.com/watch?v=_BrFKp-U8GI)
- [Group Actions](https://en.wikipedia.org/wiki/Group_action)
- [Burnside's Lemma](https://en.wikipedia.org/wiki/Burnside%27s_lemma)
- [Orbit Stabilizer Theorem](https://en.wikipedia.org/wiki/Orbit-stabilizer_theorem)