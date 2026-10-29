# Interview Cheat Sheet

From Andrei Neagoie's *Master the Coding Interview: Data Structures + Algorithms*.

## The Three Pillars of Good Code

1. Readability
2. Time complexity
3. Space complexity

## What Interviewers Look For

- **Analytical skills:** Can you think through problems and analyze them?
- **Coding skills:** Can you write clean, simple, organized, readable code?
- **Technical knowledge:** Do you know the fundamentals of the job you're applying for?
- **Communication skills:** Does your personality fit the company's culture?

## Step by Step Through a Problem

1. **Capture the key details.** When the interviewer gives you the question, write down its key points at the top (for example, whether the array is sorted). Make sure you understand the details and show that you are organized.
2. **Confirm the inputs and outputs.** Double-check what the inputs are and what the expected outputs should be.
3. **Identify the goal and constraints.** Ask what matters most in the problem, including time, space, and memory constraints.
4. **Ask focused questions.** Avoid asking too many questions.
5. **Start with a naive approach.** Explain the first brute-force solution that comes to mind. This shows how you think critically. You do not need to write this version of the code; explain it aloud.
6. **Explain its drawbacks.** Describe why the initial approach may not be ideal, such as having `O(n^2)` or worse time complexity or being difficult to read.
7. **Look for ways to improve it.** Walk through your approach, add comments where helpful, and look for repeated work, bottlenecks, or unnecessary steps. Use all the information the interviewer gave you. A bottleneck is the part of the code with the highest Big O cost; focus on improving it. Repeated work can also be a bottleneck.
8. **Outline the steps before coding.** Walk through your solution and write down the steps you plan to follow.
9. **Make the code modular.** Break it into small, clear pieces from the beginning. Add comments when they help.
10. **Start coding once you understand the approach.** Preparing the steps first can make a whiteboard interview easier. Avoid starting before you know how the solution should work.
11. **Show what you can do if time is limited.** Some interview questions cannot be fully solved in the time available. Break the problem into functions where possible. If you cannot remember a method, use a placeholder function and keep moving. Start with the parts you can solve.
12. **Consider errors and edge cases.** Do not make assumptions about the input. Think about invalid inputs and how to protect the function. You can note the checks you would add, implement the function, and explain that you would write tests to make it fail on invalid cases.
13. **Use clear names.** Avoid confusing names such as `i` and `j` when more descriptive names would make the code easier to read.
14. **Test and challenge your solution.** Consider missing parameters, `0`, `undefined`, `null`, very large arrays, and asynchronous code. Ask whether assumptions about the input are allowed. Consider whether the function should return an error, whether the solution has holes, and whether it repeats work.
15. **Discuss possible improvements.** Explain whether the solution works, whether another approach might be better, whether it is readable, and how its performance could improve. You can ask the interviewer what solutions to this problem they find interesting.

If the interviewer is happy with the solution, the interview may end there. They may also ask how you would handle input that is too large to fit in memory or that arrives as a stream. For large-scale problems, one possible approach is divide and conquer: process selected chunks from disk, write intermediate results back to disk, and combine them later. Distributed processing may also be used.

## Good Code Checklist

- [x] It works.
- [x] It uses data structures effectively.
- [x] It reuses code and avoids repetition (DRY: “Don't Repeat Yourself”).
- [x] It is modular, which improves readability, maintainability, and testability.
- [x] It avoids `O(n^2)` complexity when possible. Nested loops can be expensive; two separate loops are often preferable to two nested loops.
- [x] It uses space efficiently. Recursion can cause a stack overflow, and copying large arrays can exceed available memory.

## Heuristics for Solving Interview Questions

- [x] Consider hash maps when you need to improve lookup time.
- [x] For sorted data, consider binary search to achieve `O(log n)` search time. Binary search is an example of divide and conquer: divide the data into smaller parts and repeat the process on a subset.
- [x] Consider sorting the input.
- [x] Hash tables and precomputed information (such as sorted data) can help optimize code.
- [x] Consider the time-space tradeoff. Storing extra state in memory can sometimes reduce running time.
- [x] Follow the interviewer's advice and hints.
- [x] Hash tables often provide a space-time tradeoff: using more memory can make a process faster.

## Remember

Communicate your thought process as much as possible. Do not worry about finishing quickly; every part of the interview matters.
