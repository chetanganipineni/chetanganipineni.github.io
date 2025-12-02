---
title: "Counting Incomplete 3D Connected Cubes"
date: 2025-11-30
tags: [math, geometry]
---

From my office, I saw this problem, which is based on a 3Blue1Brown video, posted on a colleague's desk:

"Consider the set of all incomplete, open cubes thar are also 3-D, connected, and rotationally unique. What is the size of this set?

Definitions:
Open-Cube: Only the edges are present, no faces

3-D: At least on edge along each of the 3 dimensions

Connected: Singular structure

Rotationally Unique: Two structures that can be rotated to look the same are considered identical
"

I decided to take a jab at this problem in my free time. And luckily after a couple of months, I was able to solve it. In this post, I'll share my solution and thought process.

**Disclaimer:** I tried to limit my use of computers for this problem, but I did use it to solve a portion of it.

### Initial Thoughts

Immediately, when I read the problem, I thought it had to be related to Burnside's Lemma, which is a counting technique often used to solve problems involving symmetry.

The formula for Burnside's Lemma is:

\[|X/G| = \frac{1}{|G|} \sum_{g \in G} |X^g|\]

I won't go into all the details of this lemma, as you need to know group actions to fully understand it.

The following is the code block for solving one part:

## Implementation

```python

def incomplete_3d_connected_cube_count():
    # used to check if cude is 3d
    is_x_visited = [False]
    is_y_visited = [False]
    is_z_visited = [False]

    all_incomplete_cubes = set()
    visited = set()



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
        #now check if all visited contains x,y,z
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

    for start_node in adj_matrix.keys():
        dfs(start_node)

    return len(all_incomplete_cubes) - 1 #removing complete cube

```