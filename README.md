KhataPe Lending Decisions: Direct Answers vs Chain-of-Thought Prompting

A FinTech case study on when AI can give a quick answer and when it must show its working.

Author: Ankush · BBA (FinTech), Chitkara Business School · Tool: Claude · November 2026

The case

KhataPe (fictional) is a digital lender in Indore that lends to kirana shops and students. Every month it must choose between two loan products with different interest rates, fees and default risk. As a Business Analyst, I tested whether AI can pick the more profitable option, and whether asking it to reason step by step makes it more reliable.

The data

8 synthetic monthly scenarios created with AI, including 3 "trap" scenarios (S02, S04, S06) where the higher interest rate makes less profit, and 1 tie (S07). I calculated the correct answers myself in a spreadsheet before testing the AI.

Decision rule

Net return = Interest rate + Processing fee − Expected default − Cost of funds
Profit = Net return × Loan budget
Tie rule: if profits are equal, choose the option with the lower expected default.

Approach
Step	Prompt type	Task
1	Direct	Which option has the higher interest rate?
2	Direct	Which option makes more profit? (final answer only)
3	Chain-of-thought	Same decision, solved step by step
4	Chain-of-thought	One number changed: does the AI update every step?
Results
Metric	Direct	Step by step
Correct choice (/8)	8	8
Correct profit figure (/8)	8	8
Trap scenarios correct (/3)	3	3
Working I could check	No	Yes
Change-one-number test

In S01, I raised Option B's expected default from 6% to 10%. The AI updated every step: B's net return fell from 8% to 4%, its profit fell from ₹3.60 crore to ₹1.80 crore, and the choice changed from B to A.

Key learnings
A direct answer is enough for one-step questions: The higher-interest question only compares two numbers per row. The AI got 8/8 (B in every scenario except S05) with no working needed.
Step-by-step reasoning helps multi-step decisions: In this test it fixed none of the scenarios, because the direct profit-based choices were already 8/8, including the traps and the S07 tie. Its value was that every net return and profit became checkable, which matters more as decisions get harder.
Convincing is not the same as correct: I found no wrong step. The working was convincing and also correct. In S07, A and B both earn an 8% net return (₹4.40 crore), and the working applies the tie rule (A's default of 4% against B's 9%) to choose A, which matches my sheet. With only 8 scenarios, I cannot conclude that direct answers are reliable in general.
What the numbers do not show: RBI digital lending rules (APR and fee disclosure, limits on default-loss guarantees with partners) and collection and servicing costs, which typically rise with higher-default products.
My recommendation to KhataPe

Use AI to produce the monthly comparison with step-by-step working, so each net return and profit can be traced. A human should verify the numbers against a spreadsheet, confirm the tie rule was applied, and review regulatory compliance and collection costs before any product is chosen.

Skills shown

Prompt engineering · Chain-of-thought prompting · Synthetic data creation · Spreadsheet financial analysis · AI output verification · Lending business basics

What I learned
A direct prompt works well for simple, one-step questions.
Chain-of-thought prompting makes AI show each step, so I can check its working instead of trusting one number.
Step-by-step working can look convincing even when a number is wrong, so every step must be checked. I found no errors in this test, but I checked all eight scenarios.
How to create synthetic business scenarios with AI, including deliberate "trap" cases.
Why I calculate my own answer key in a spreadsheet before testing AI.
Changing one number is a quick test of whether AI really reasons or just repeats. Here, every step updated correctly.
Numbers alone do not make a lending decision; risk and regulation matter too.

KhataPe and all data in this project are fictional and created for learning.
