
## Introduction
These rules of data science are intended as advice to make you a better data scientist or better understand data science if you work with data scientists. Some of them are facts (eg. "models are terrible at extrapolation") and some of them are heuristics (eg. "You will be better at data science if you think of it as decision science").

In the interests of memorability each `rule` is listed as a pithy, single-sentence assertion.

Of course, single-sentence assertions are neither evidence nor a particularly good way for a reader to understand the underlying dynamics if the assertion does not immediately resonate with their own experience.  Therefore you can click each "Rule" to open an expanded section that briefly explains the reasoning behind it.  These sections are a balance between brevity and completeness that leans towards brevity at the expense of considering all edge cases or when the rule might not apply; I want to equip you with enough information to decide if & when you will make use of the rule.  Even I do not think these are cast iron rules that are true in all situations all of the time (although some of them are close to it!), be thoughtful and make use of them as best suits you.



## :books: The Rules of Data Science :books:
<details>
  <summary><b>You will be better at data science if you think of it as decision science.</b></summary> 
  
  The most important part of data science is the “so what?” of your discovery.  What should be done differently because of this, and how can that change be realised?  Seen this way, the entire toolkit of data science is focused on making better decisions and changing outcomes.

  For example, consider a model to forecast industrial equipment failures. It can be tempting to think of improving the accuracy of a model as a KPI that proves we have done well, but it isn’t: what matters is how much the model improves the real world result, what decision it allows us to make differently that creates value.  It might not be valuable to forecast equipment failures more accurately if the forecast is significantly shorter than the lead time to deliver and install the part (downtime due to breakages is unchanged), or if precision:recall tradeoffs determine value more than does accuracy, or any one of a number of complications unique to the equipment we are trying to forecast failure on.
  
  The entire problem of “forecasting equipment failure” should have been considered as “how to maximise the value of the equipment?” and the overall context analysed to look for decisions that might be altered to create value:  AI to forecast equipment failure at the individual level, analysis of which maintenance activities are most impactful, changing the intensity at which equipment runs to arbitrage lifespan against productivity, flexible schedules on maintenance teams, altering the distribution of parts in warehouses, etc…  
  
  Thinking of the core problem as finding the right decision and then making it correctly expands the data scientist’s view in impactful ways.  Talk to stakeholders to understand the operations we will be changing, create consensus among change leaders who need to believe in a project for it to work, reject modelling efforts that can’t be impactful even if accurate.
  
  In the average project most of the value comes from a good understanding of the business problem, the product and the data, combined with the interpersonal skills to get stakeholders to commit to the correct decision.
</details>


<details>
  <summary><b>Any data source will degrade to the point marginally above where it impacts business critical activities and KPIs.</b></summary> 
  
  AKA **Burley’s Law of Data Degradation** (I talk about this one a lot...).

  Overall, the quality of a company’s data will degrade to the point just shy of impacting daily operations.  The data that a business needs for mission-critical operations will be in good working order and the data that does not impact critical initiatives will almost certainly not be.
  
  There are two main reasons for this: 
  1) human work invariably has mistakes and mission-critical data gets checked in a way that non-critical data does not, thus the latter accumulates errors over time; 
  2) traditional business logic viewed IT as a cost be minimised and therefore smart IT policy was to only invest in mission critical systems.  
  
  As a data scientist, internalising this fundamental paranoia about data sources is one of the key ways experienced staff are better at the job.  

  On a technical level, project timelines should include significant data cleaning ([data understanding](internal link to rule)) for a new product and ongoing products need a plan to maintain data quality.

  On a professional level, data scientists should accept that an existing data source being below the quality we need is rarely due to malice or incompetence; it is the result of a smart prioritisation of resources.  Take time to understand why things are the way they are and you will be a better collaborator and get great results faster.
</details>

<details>
  <summary><b>Comment code so an idiot can understand it (the idiot will probably be you).</b></summary> 
  
  Closely related to Guido Van Rossum’s famous _“code is read more often than it is written”_, we should make our code as unambiguous as possible.  It is rarely an inefficient use of time to typehint, write detailed docstrings, and add comments.  The writer will spend far less time on the commenting than the next reader will spend understanding the code.

  In case further motivation were needed, the time you save is most often your own when you come back to use/modify your own prior work.  Furthermore, the process of writing typehints and comments will often make you realise something is unnecessarily unclear, inefficient or inextensible and allow immediate corrections.
</details>

<details>
  <summary><b>People are expensive, computers are cheap.</b></summary> 
  
  A data scientist or software engineer costs tens-to-hundreds of $/£/€ per hour and storage+compute cost orders of magnitude less.  
  
  Bear this in mind when thinking of optimisations -- spending a week of person-time to save $10pcm on cloud fees is a terrible investment.  The best optimisations are ones that make staff more efficient.  We should be happy to pay for more compute resources to fix a problem or leave code slower than it could be, because this is how we make the most value long term.
  
 The justifiable times to work on compute efficiency options typically are one of following, which are (mostly) about identifying the downstream effects of inefficient code rather than the direct cost:
  
   -  "A stitch in time saves nine":  A refactor now is much simpler than later, so the work is a people-saving measure.  We are favorably arbitraging current vs future person time.
   -  "Loathed systems": Human concentration can be a fragile thing and waiting on a compute process for 5 mins can ruin human workflows. As can instability, unclear UX or bad error handling.  When there is a process users don't like, consider improving the code quality.
   -  "Business critical":  A few extra hours of compute time doesn't matter until it is the difference between an overnight system update being ready for business in the morning.  We are not worried about the compute cost, we are worried about a business revenue stream.
   - "Actually computers are expensive":  Sometimes the monthly compute bill is larger than staff costs (you'll know if it is) and compute efficiencies are well worth the staff time they require.
  
 To be clear, this rule is **not** an excuse to rapidly write shoddy code (that will mire your team in technical debt and scaling problems), nor is it an excuse for management to allow a rickety codebase to persist unpatched and barely stable.  It is about making decisions that best make use of the resources available to us taking an accurate view of their costs, and offering a heavy reminder that we frequently underestimate the expensive of our staff.
  
</details>

<details>
  <summary><b>Machine Learning is rebranded statistics.</b></summary> 
  
  The business use of statistics used to be hours-to-months of human time in order to make a prediction or determine if a hypothesis was true.  It required data that was causally related to the problem and, at best, Mutually-Exclusive & Completely Exhaustive (MECE).

  It is a useful cognitive lens to view machine learning as a mathematical system that does statistics very quickly to make a prediction.  All the same caveats for data apply: do you think the inputs to the ML model present a complete knowledge of the causal inputs to this prediction?  For data scientists this can suggest which data source you need to curate.  For people working with data scientists you can ask in detail about model inputs and consider if you would trust human statisticians’ predictions using those data?  If not, you might want to be careful about relying on that model.
</details>

<details>
  <summary><b>Models are (almost never) a true understanding of the underlying dynamics. </b></summary> 
  
  AKA _“All models are wrong, but some models are useful.”_

  See: next two rules ”Models are terrible at extrapolation” “Models are a snapshot of inferred relationships”.  Best practice in response to this is understanding & accepting those limitations and planning accordingly.

  At time of writing (Dec 2022), this rule is correct.  But we may see future model architectures that can better provide causative understanding of systems and extrapolate in a more reasonable fashion.
</details>

<details>
  <summary><b>Models are terrible at extrapolation.</b></summary> 
  
  Machine learning models work by freeform fitting to observed data (save rare examples where you embed a causal structure in the model: say enforcing a radial kernel in a SVM or the recent “physically-motivated neural network” trend).  We can think of this, fairly accurately, as creating a very long complex formula to interpolate between known datapoints (train set) to perform well on similar datapoints (test set).

  There is no reason to believe that such interpolation-based modelling will extrapolate to uncharted parts of the input hyperspace and give correct (or even sensible) results.  ML is much like fitting a polynomial to a wiggly line: amazing results within the seen data range, dangerous results outside of that range.  The exact nature of that danger depends on the model (eg. decision tree vs linear regression) and all data scientists should be alert to not trust models when they are extrapolating.
</details>

<details>
  <summary><b>Models are a snapshot of inferred relationships.</b></summary> 

  Models optimise to match the results seen in their input data, based on the mathematical structure of the model.  They do not posit any true causal understanding of the relationships between variables or how those relationships might change when unseen external factors alter.  

  Famously, Google Flu Trends could forecast upcoming flu rates based on internet search terms -- an eminently sensible idea: flu rates should be related to searching about illness symptoms, trips to pharmacies and all sorts of data that Google knows -- but the project failed over 2013-15 with epidemic flu seasons when fear changed how people searched for flu.

  This problem can be defended against by proactively retraining models on new data, giving the model truly MECE data (but beware that extrapolation is still a problem), structuring models with true causal understanding, or by honestly admitting that a model is imperfect and planning its use aware that future real-world changes will break it.
</details>

<details>
  <summary><b>Data cleaning is actually data understanding.</b></summary> 
  
  Cleaning is, for most of us, an unfortunate chore (happy to have it done but rarely happy about doing it) and framing part of our data science workflow as "cleaning" creates an aversion that is harmful.

  "Cleaning" implies that the cleaned data is sole result, that the data starting off dirty was an aberrant mistake if we could get a genie to magic up clean data with no human memory of how it was cleaned we could be productive data scientists focused on the "real work".

  But data cleaning is selectively choosing and applying tranformations to create the best possible MECE dataset for downstream analysis and models.  And that is anything but trivial, it's the foundation for decision-making (recall we are really decision scientists).  Doing that means understanding the data, and considered that way it is obvious that "cleaning" isn't a menial chore but one of the most important parts of getting a good model. That's an important mindset change that make you more attentive and happier when doing it.

  Data cleaning is therefore data understanding (and all the actions you take after understanding the data) and you can't possibly skip "understanding" when doing data science.

  There are some important corollaries to knowing that cleaning is about understanding the dataset:
   - knowledge of the data is as important as the transformations applied, document those important pieces of provenance and data-gotchas;
   - every choice made in data cleaning should be documented;
   - cleaning transforms are as important as feature engineering transforms (they should be reusable and well-commented).
</details>

<details>
  <summary><b>End users are more important than the model.</b></summary> 
  
  [link to decision bit; models/findings only have impact if used/implemented;  should talk to people before during and after model design.]
</details>

<details>
  <summary><b>Be a positive collaborator with non data scientists.</b></summary> 
  
  When a data scientist starts looking into a topic at a company, we have a nasty habit of finding all the accumulated mistakes and generating extra work for other staff as we investigate why data is the way it is.  Depending on the mistakes found, staff might fear we are damaging their reputation and career.  Approach this the wrong way and people will not be enthusiastic collaborators.

  Best practice is to focus on the improvements that can be made (not past mistakes), have empathy for the past constraints and openly praise the great work that you find in your investigations.  If reporting fundamental shortcomings to management, be honest but explain the “why” of how we got there and the path to improvement.  This will get everyone better results faster and is the first step on making a transformation to a data-driven division/company.
</details>

<details>
  <summary><b>Try to make your boss redundant.</b></summary> 
  
  Which could be rephrased as “anticipate your boss’ needs”. This is not a data science specific rule, but is important enough to include regardless.

  Typically your boss will spend some amount of time thinking about your work: verifying correctness, deciding the next priority, tracking timelines, (etc…), and some amount of time doing differentiated work that only she can do:  her own technical work, planning organisation-level resources, getting buy-in on projects and removing roadblocks.  The more you can proactively take over the former tasks such that your boss doesn’t have to do them, or you provide curated inputs to make her tasks faster, the better.  This will make you more aware of the context of your work within the larger organisation (always good personal growth) and is commonly aligned with promotion requirements in larger companies.  Plus, if your company is well-organised you are enabling both you and your boss to spend more time on more valuable work
</details>



<details>
  <summary><b>Template.</b></summary> 
  
  Explanatory text
</details>




## Why should you trust my opinions? 🤔
You probably shouldn’t trust anyone’s opinions purely from their background (there a [logical fallacy](https://en.wikipedia.org/wiki/Argument_from_authority) about that), but background certainly helps set a baseline expectation of reliability.

I’ve spent >15 years on science, strategy consulting, building models of physical processes, and data science.  My time in strategy consulting was when [“big data” became a thing](https://trends.google.com/trends/explore?date=all&geo=US&q=big%20data) and I was the frontline consultant doing analysis and creating new methods in my firm.  I ran data science projects in the Foundry.ai studio building prototype AI systems with several Fortune 500 companies and spoke with people from CEOs, through division heads, to frontline staff to make AI projects with positive ROI within 12 months.  Currently, I am head of data science at a start-up with a few million in revenue.  

I also did well on the UK nationally televised TV quiz “University Challenge”, which sounds like it should be irrelevant, save that the weird brain trick of being good at quizzes is about collating information and synthesising patterns into best guesses,  which is basically what a “Rules of Data Science” is.
