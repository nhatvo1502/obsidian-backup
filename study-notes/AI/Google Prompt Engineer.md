# Module 4: Design great prompt

Persona
Task
Format
Context

#### Three C's while prompting
*1. Be concise:* Keep prompts simple and avoid overly long or complex requests in a single prompt. A prompt that is short and to the point generally requires less processing from AI
*2. Be clear:* Be precise and avoid contradictory or ambiguous instructions. Vague prompts. like "Make this better," give AI too many possible paths and require it to make assumptions. Instead, give clear
*3. Be consistent:* Use the same vocabulary for the same concepts throughout your conversation with AI. For example, if you refer to a "spreadsheet" in your initial prompt, continue to say "spreadsheet" throughout the rest of your conversation. Using words like "matrix" or "sheet" interchangeably in the same chat might confuse AI.

#### Evaluate the output
*1. Accuracy:* is the info correct and factually correct?
*2. Bias:* does the output favor one perspective unfairly because of its training data?
*3. Relevancy:* does it directly answer prompt and stay on topic?
*4. Consistency:* is the tone, style, and quality the same throughout the response?

#### Iteration
*1. Revisit the prompting framework:* If prompt is not giving satisfied result, edit and add more detail to persona, task, format, or context.
*2. Break up complex tasks:* Avoid asking everything at once. Ask for smaller pieces of the task, one at a time. 
*3. Add constraints:* Add the specific requirements that AI must meet to narrow the focus of the response

#### Use references to model desired result
*References* should:
	* Provide examples or resources that illustrate what you want AI to produce.
	* Specifying details about desired output: style, tome, and format
	* Including text, images, audio, or even video as a reference

#### Use new chat for each new topics
Using new chat will ensure the context window is limited to how much information AI can retain and refer back to within a single chat. It allows AI to refer back to earlier parts of the conversation so its answers stay consistent. Switching to a new topic within the same chat will cause the AI to generate an irrelevant or misguided response.

#### Save your best prompt in a prompt library
Like any skill, prompting abilities will improve through experimentation and practice. Save the best prompt and reuse it will save time.

### C. Prompting Trick
"Please ask me any follow-up or clarifying questions ​before you continue doing work."
"Okay, well, actually what about this task do I not know ​and I need to ask me, the user?"


# Module 5: Level up prompts
## Prompt chaining strategies
Two advanced techniques:
*1. Powerful prompt phrases:* Using specific and precise language inside a single prompt to improve the quality and depth of AI's response
*2. Prompt chaining:* Using smaller and connected prompts to structure an entire conversation and break down a missive project

## Guide AI with powerful prompt phrases

**Give AI a process to follow**
* Think step-by-step
* First, [action 1]. Second, [action 2]. Finally, [action 3]

**Define the audience and tone**
* Write this for an audience of [audience type]
* The tone should be [professional, casual]

**Set hard constraints**
* Write a one paragraph summary
* Focus exclusively on [revenue, tech stack] and do not mention [cost, pricing]

**Request a critique**
* Critique this text from the perspective of a [role, e.g, potential customer]
* Play devil's advocate. What is the strongest counterargument to this?

**Generate alternatives**
* Give me 3 different versions of this
* What's an alternative approach to solving this problem?

**Deepen or expand on the initial output**
* Elaborate on point 2
* Provide more detail and specific examples for the section about [section]

## Manage more complex tasks with prompt chaining
Some tasks are too big for a single prompt. Prompt chaining helps you tackle large tasks by breaking them into a series of smaller, connected steps that are all in the same chat. It works like a factory assembly line: The output from one prompt is used as the input for the next, linking all steps together like a chain.

**Prompt 1:** I'm going to Paris for 3 days. I like art, historical sites, and parks. Suggest a few well-known places I could visit on my trip.
**Prompt 2:**  Using those locations, create a logical day-by-day itinerary that minimize travel time.
**Prompt 3:** For reach day of the itinerary, suggest a few restaurants located near the suggested locations.

-> Breaking the task into logical, digestable steps and using the output of one prompt as the specific input for the next, you transform AI from a simpler answer generator into a structured collaborator.

## Advance prompt chaining
**1. Strategic collaboration:** Learn to use AI as a thought partner that can critique and refine your strategy rather than just execute simple commands.
**2. Complex problem solving:** Master the skill of breaking down overwhelming projects into clear and connected phrases that build toward a final goal
**3. Stronger outputs:** Discover how layering information over multiple attempts leads to deeper and more tailored results compared to a sinle, one-off request