---
layout: post
title: Teaching Object-Oriented Programming
date: '2008-10-30T16:00:00.000-10:00'
author: Christopher Slade
tags: 
  - teaching 
  - beginning programming 
  - oo programming
description: Since a lot of our students come here with very little computer experience, we had our beginning programming course split into two courses.  The first half focused on variables and control structures, and the second half focused on object-oriented programming with C++.  Some time last year we decided to teach a scripting language (Perl) in the first course due to it's simplicity -- hello world is only one line.  We then created a two course series in object-oriented programming in Java.  This would allow us to make sure our students had a solid object-oriented background and three classes to develop their programming and problem solving skills, something that takes a lot of practice.
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-6863005831936869442
blogger_orig_url: https://www.christopherslade.com/2008/10/teaching-object-oriented-programming.html
redirect_from: /2008/10/teaching-object-oriented-programming.html
---

Since a lot of our students come here with very little computer experience, we had our beginning programming course split into two courses.  The first half focused on variables and control structures, and the second half focused on object-oriented programming with C++.  Some time last year we decided to teach a scripting language (Perl) in the first course due to it's simplicity -- hello world is only one line.  We then created a two course series in object-oriented programming in Java.  This would allow us to make sure our students had a solid object-oriented background and three classes to develop their programming and problem solving skills, something that takes a lot of practice.

During the summer, I spent a lot of time creating labs and planning lectures for this new Java course.  After my Java class today, I had a discussion with a few struggling students.  After listening to their comments, I realized I had made a mistake on how I organized the class.  I decided to follow what most textbooks suggest and even brag about, focus on objects right at the beginning.  To me, this sounded like the best way to explain objects and classes.  An object is just like an object in the real world.  It has a nice interface and you just tell it what to do and it does it.

Today, I realized a major problem with this. They are still trying to grasp the concept of methods, and now they have to put the method in one file and the call in another.  They are still trying to grasp the concept of a variables, and now they put the declaration at the top of a class, and then use them inside the methods.  Plus, when they want to use a variable they are probably writing their main method and the variable is hidden in another file.  On top of all of this, they are trying to solve a problem.  Try working out a math problem on a bunch of different puzzle pieces and then put the pieces together in the right order to form a solution.  Thinking back to my beginning programming class, I remember struggling with the same thing when I first learned about objects and classes.

So here is my solution.  First, teach them about variables and how to use them.  Next focus on types, and then control structures, methods, and arrays.  Then present the idea of an object and class.  But first, as just a bunch of different variables that are related (like a struct).  What might work best is an example of keeping track of students -  their names, ids, and addresses.  Isn't it a lot of work to declare a string for each student and a int for their id and another string for their address and somehow keep them related?  Wouldn't it be nice to have all of those grouped together in an "array"?  Well we can, it's called an object.  Make the member variables public and use them like any other variable.  Next explain how it would be nice if the address edit method was somehow grouped with the student as well.  Then explain the constructor, and work towards encapsulation.

This way, the student first learns the basics without the need to memorize where everything goes.  They also learn object-oriented programming the same way it was invented, which shows the value of object-oriented programming.  Show them the structured programming way, and then show them how object-oriented programming improves upon it and simplifies the code.  By thinking that the why of oo-programming is to complex to explain, I actually made oo-programming more confusing.

Now I have to reorganize my class for next semester.