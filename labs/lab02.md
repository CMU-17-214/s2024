# Lab 2: Encapsulation

In this lab you will get familiar with core language features for encapsulation in Java and practice with encapsulation and information hiding.



## Deliverables

- [ ] Rewrite the Java implementation to improve encapsulation. The code should hide implementation details with language mechanisms.
- [ ] Adjust the code to use interfaces instead of direct implementations while maintaining functionality. 
- [ ] Demonstrate your understanding of good commit practices with the commits solving this encapsulation task.



## Good Git Practices 

Recall good practices for git and commit messages from the lecture. Good practices help you and other engineers understand your development process. Especially:

- Make clean, single purpose commits.
- Leave meaningful but concise commit messages. 
- Commit early, commit often
- Don’t alter published history
- Don’t commit generated files 

Demonstrate those practices with all commits you do in this lab and also in all future homework assignments.



## Improving Encapsulation

Fork and clone this repository: [https://github.com/CMU-17-214/s24-lab02.](https://github.com/CMU-17-214/s24-lab02.git)

First, get familiar with the source code. Find the entry point, follow imports, and understand classes/types used. Run the code (recall Recitation 1 for instructions). Generally the code is structured as follows:

- The `shapes/` folder contains the Shape interface and several implementing classes.
- A `Renderer` class takes a `Rectangle` object and provides a `draw` method.
- `Main.java` creates a `Renderer` backed by a `Rectangle` and calls `draw()` on it.



Second, look for problems—no code is perfect, even if it works. In this case, we are looking for issues related to encapsulation & information hiding. Check whether any code is either accessing or depending on information that is not essential to its functioning. To put it differently, could the code be made to work while assuming access to fewer implementation details. *Hints: What type of Shape does a Renderer actually need, in the real world? Does the implementation depend on something more specific, for instance by accessing information it shouldn’t rely on?*



Third, rewrite the code to improve encapsulation and information hiding. Here are some suggestions:

1. First, consider what a better design of the shapes/ package would look like: What would a common interface for a shape look like?
2. Once you introduce the proper interface, you can make the changes to the implementing classes to both (a) implement that interface precisely, and (b) hide *all* information that is not part of the interface.
3. Finally, find all *uses* of shapes and ensure that they depend only on the interface and not on any internals. Also think about *declaring types:* if you’ve made all the changes correctly, your main function no longer needs to provide Rectangle to Renderer, so it should declare the shapes as Shapes, even if they are *instantiated* as something more specific.



Finally, commit your solution using good commit practices (see our [Git instructions](git-basics.md) if needed).
