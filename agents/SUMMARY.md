# Paper Notes

## Practices for Governing Agentic AI Systems

**Authors**: Yonadav Shavit, Sandhini Agarwal, Miles Brundage, et al.

**Link**: [Paper](papers/practices-for-governing-agentic-ai-systems.pdf)

### Summary

This white paper provides a framework for responsibly integrating agentic AI systems (AI systems that can pursue complex goals with limited direct supervision) into society. Key aspects:

- **Definition & Scope**:
  - Defines agentic AI systems and their lifecycle
  - Identifies key stakeholders and their responsibilities
  - Focuses on baseline safety practices and governance

- **Key Safety Practices**:
  1. Task Suitability Evaluation
  2. Action-Space Constraints and Approval Requirements
  3. Default Behavior Settings
  4. Activity Legibility
  5. Automatic Monitoring
  6. Attributability
  7. Interruptibility and Control Maintenance

- **Agent Evaluation**:
  - Highlights unique challenges in evaluating agentic systems
  - Recommends breaking down evaluation into subtasks (e.g., information gathering, calculations, reasoning)
  - Suggests prioritizing evaluation of high-risk actions
  - Notes that rare failures can compound in long action sequences

### Significance

The paper establishes foundational guidelines for governing agentic AI systems, emphasizing the importance of safety, accountability, and responsible deployment. It acknowledges both the potential benefits and risks of these systems while providing practical recommendations for their governance.

## Magentic-One: A Generalist Multi-Agent System for Solving Complex Tasks

**Authors**: Adam Fourney, Gagan Bansal, Hussein Mozannar, Cheng Tan, et al.

**Link**: [Paper](papers/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks.html)

### Summary

Magentic-One is an open-source multi-agent system designed to solve complex tasks through effective planning, multi-step reasoning, and error recovery. Key aspects:

- **Architecture**: Uses a lead agent called the "Orchestrator" that:
  - Plans and tracks progress
  - Re-plans when errors occur
  - Coordinates specialized agents for specific tasks (web browsing, file handling, coding)

- **Key Features**:
  - Modular design allowing easy addition/removal of agents
  - No need for prompt tuning or training when modifying the agent team
  - Competitive performance with state-of-the-art on multiple benchmarks (GAIA, AssistantBench, WebArena)
  - Demonstrates progress toward generalist agentic systems

- **Tools**:
  - Includes AutoGenBench for rigorous agent evaluation
  - Provides controls for repetition and isolation in benchmarking
  - Open-source implementation available at https://aka.ms/magentic-one

### Significance

The paper demonstrates that a well-designed multi-agent system can achieve high performance across diverse tasks without requiring task-specific modifications to core capabilities or collaboration mechanisms. This suggests a promising direction for developing more general-purpose AI systems.