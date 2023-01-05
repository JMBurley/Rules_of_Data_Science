# Rules of Data Science

## Introduction
These rules of data science are intended as advice to make you a better data scientist or better understand data science if you work with data scientists. Some of them are facts (eg. "models are terrible at extrapolation") and some of them are heuristics (eg. "You will be better at data science if you think of it as decision science").  Each of these `rules` is something I have high certainty is important and will make a meaningful change to the quality of work you output.

In the interests of memorability each `rule` is listed as a pithy, single-sentence assertion.

Of course, single-sentence assertions are neither evidence nor a particularly good way for a reader to understand the underlying dynamics if the assertion does not immediately resonate with their own experience.  Therefore you can click each "Rule" to open an expanded section that briefly explains the reasoning behind it.  These sections are a balance between brevity and completeness that leans towards brevity at the expense of considering all edge cases or when the rule might not apply; I want to equip you with enough information to decide when & if you will make use of the rule.  Even I do not think these are cast iron rules that are true in all situations all of the time (although some of them are close to it!), be thoughtful and make use of them as best suits you.


## Why should you trust my opinions?
You probably shouldn’t trust anyone’s opinions purely from their background (there a [logical fallacy](https://en.wikipedia.org/wiki/Argument_from_authority) about that), but background certainly helps set a baseline expectation of reliability.

I’ve spent >15 years on science, strategy consulting, building models of physical processes, and data science.  My time in strategy consulting was when [“big data” became a thing](https://trends.google.com/trends/explore?date=all&geo=US&q=big%20data) and I was the frontline consultant doing analysis and creating new methods in my firm.  I ran data science projects in the Foundry.ai studio building prototype AI systems with several Fortune 500 companies and spoke with people from CEOs, through division heads, to frontline staff to make AI projects with positive ROI within 12 months.  Currently, I am head of data science at a start-up with a few million in revenue.  

I also did well on the UK nationally televised TV quiz “University Challenge”, which sounds like it should be irrelevant, save that the weird brain trick of being good at quizzes is about collating information and synthesising patterns into best guesses,  which is basically what a “Rules of Data Science” is.


## The Rules of Data Science
<details>
  <summary><b>You will be better at data science if you think of it as decision science.</b></summary> 
  
  The most important part of data science is the “so what?” of your discovery.  What should be done differently because of this, and how can that change be realised?  Seen this way, the entire toolkit of data science is focused on making better decisions and changing outcomes.

  For example, consider a model to forecast equipment failures. It can be tempting to think of improving the accuracy of a model as a KPI that proves we have done well, but it isn’t: what matters is how much the model improves the real world result, what decision it allows us to make differently that creates value.  It might not be valuable to forecast equipment failures more accurately if the forecast is significantly shorter than the lead time to deliver and install the part (downtime due to breakages is unchanged), or if precision:recall tradeoffs determine value more than does accuracy, or any one of a number of complications unique to the equipment we are trying to forecast failure on.
  
  The entire problem of “forecasting equipment failure” should have been considered as “how to maximise the value of the equipment?” and the overall context analysed to look for decisions that might be altered to create value:  AI to forecast equipment failure at the individual level, analysis of which maintenance activities are most impactful, changing the intensity at which equipment runs to arbitrage lifespan against productivity, flexible schedules on maintenance teams, altering the distribution of parts in warehouses, etc…  
  
  Thinking of the core problem as finding the right decision and then making it correctly expands the data scientist’s view in impactful ways.  Talk to stakeholders to understand the operations we will be changing, create consensus among change leaders who need to believe in a project for it to work, reject modelling efforts that can’t be impactful even if accurate.
  
  In the average project most of the value comes from a good understanding of the business problem, the product and the data, combined with the interpersonal skills to get stakeholders to commit to the correct decision.

</details>

<details>
  <summary> *Here is a second rule* </summary>
  
  Explanatory text
   - bullet point
   - _italic_
   - *bold*
  ### Some Code
  ```python
  print('hello world')
  ```
</details>

End of doc
