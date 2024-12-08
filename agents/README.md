# Keynotes:
## Agent Evalutaion:
The field of agentic AI system evaluation is nascent, with more questions than answers, so
we offer only a few observations. Evaluating agentic AI systems raises new challenges on top of
the already significant challenges with evaluating current language models [19]. This is in part
because successful agents may often need to execute long sequences of correct actions, so that even if
individual actions would only fail infrequently, these rare events could compound and make failure in
deployment likely. One solution is for system deployers to independently test the agent's reliability
in executing each subtask. For example, when an early system deployer was building an AWS
troubleshooting agent on top of OpenAI's GPT-4 API, they broke down the agent's needed subtasks
into "information gathering," "calculations," and "reasoning," and created evaluations for each
independently. Breaking down all the subtasks that could be encountered in a complex real-world
operating domain may sometimes be too difficult for system deployers; one approach could be to
prioritize doing such evaluations for agents' use of high-risk actions, like financial transactions.

source: https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf