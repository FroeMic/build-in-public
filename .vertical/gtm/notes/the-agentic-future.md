# The Agentic Future

Status: Working note — externalized assumptions, meant to be discussable
Author: Micha
Date: 2026-07-04
Related: [the-big-cake.md](the-big-cake.md)

I took some time to summarize the assumptions I have about the future. I wanted
to externalize them and make them discussable.

## The future we believe in

- AI models enabled to interact with the real world will drive valuable outcomes.
- The demand for intelligence is near infinite.
- As a result, compute will remain scarce for a number of years.
- Scarcity is driven by supply-side constraints: GPUs (and complements) and energy.
- Developing frontier models has strong economies of scale due to scaling laws
  and pre-training compute. Frontier labs need a scaled, sustainable revenue
  stream to finance pre-training.
- We will likely end up with few scaled frontier labs.
- These frontier labs will retain their leading edge in the short- and midterm;
  highest-intelligence models will be closed source.
- Frontier-model capabilities will continue to improve at the same or a faster
  rate than the trend in the near-term (see Epoch).
- Frontier-model performance will be high-margin (80%) as demand for best
  intelligence is high and these models are differentiated.
- Open-source models will be close followers, driving down costs for tasks /
  agents that do not require frontier-model performance.
- This will drive down cost. LLM inference prices at a fixed level of
  performance will continue to fall rapidly in the short and midterm; at least
  an order of magnitude per year (last year 40x).
- Because open-source models are commoditized, deploying and serving them will
  be a low-margin business in the long-term. In the short-term, compute
  scarcity and scarcity of knowledge and experience in how to deploy them will
  create opportunity for profits in this segment.
- The resulting market structure will look similar to the smartphone market:
  few concentrated players (Apple, Samsung) capturing all profits and a
  long tail of other (open-source) players operating at / around cost.
- As inference cost becomes a significant line item for companies, they will
  invest in cheaper open-source models.
- As supply-side market concentration is already emerging today, companies
  will strive to be model-provider independent or at least
  "multi-model-provider". Business leaders are aware of this risk already today.

## Agentic computing is becoming a new compute paradigm

Next to deterministic software execution.

- What is agentic computing? Operating procedures and policies are written
  down in natural language [instead of deterministic code] and interpreted by
  probabilistic LLMs.
- Most compute, most tokens, most internet traffic will be produced and
  consumed by agents.
- There will be a lot more data / traffic / code.
- There will be user-facing applications / agents AND there will be background
  agents.
- Most compute will be used by background agents.
- The rise of background agents will be driven by application-layer value
  creation shifting from productivity boosts for humans (co-pilot) to doing
  the actual work.
- The requirements for inference compute consumed by background agents will be
  different from user-facing agents / applications. Latency and speed will be
  less important for background agents because there is no UX.
- These weaker requirements will enable long productive lifetimes of older GPU
  generations already deployed today and drive new deployments (e.g.
  datacenters in remote locations; datacenters in space).
- Durable workflows will be a central element of agentic software.
- Transaction costs between agents will approach near zero as they are a
  central complement to the actual agentic value creation (law of tech:
  commoditize your complement).
- Consequently, to win in A2A business models you need to build a scaled
  cost-leader.
- Deterministic software itself loses pricing power; it is becoming
  commoditized.
- User interfaces will be generated dynamically and will be personalized to
  user and/or use-case.
- The data layer / access layer through which to access data will be sticky.
  It will be the stable fundament for agents and for generating (ephemeral)
  user interfaces.

## The predominant organizing principle of companies will shift towards AI-native companies

- A company becomes AI-native when its work is no longer routed through human
  memory, meetings, and management layers, but through machine-readable
  context, goals, tools, and closed feedback loops. Humans will continue to
  set direction, taste, trust, and constraints. Agents do more and more of the
  work.
- In AI-native companies middle management will disappear; employees instead
  will be highly leveraged individual contributors coordinating through the AI
  layer.
- AI-native companies, if built right, can become recursively self-improving
  and automatically reap the benefits of model improvements.
- At the extreme, companies may become autonomous: they self-direct without
  any human involvement. In the short and mid-term society will not tolerate
  companies that are completely owned and/or run by AI.
- Today, most companies are not aware of / not striving towards becoming
  AI-native. Most companies are still focused on becoming AI-assisted, i.e.
  increasing the productivity of their workforce with AI. Either companies
  adopt an AI-native organization or they miss most benefits of AI and thus
  lose in competitiveness.
- Organizational inertia will cause large companies to embrace this shift only
  slowly. Because it requires changing the core structure and processes of the
  organization, people will resist it.
- Building things for AI-native companies today is likely a zero-billion-dollar
  market opportunity.

What does an AI-native company need?
- Internal company agents
- Software factory
- Sensors to the outside world (integrations: reading)
- Actuators to affect the outside world (integrations: writing, people)
- A company brain (data capture + translation into artefacts)

## Generalists will thrive in a new economy, enabled by AI agents

- It will become much easier to build things, for everyone. Compared to pre-AI
  software engineering, there will be 1000x more builders empowered by AI.
- The creator economy will expand even more. Creators, today primarily
  entertainers and educators, will grow into new domains related to building.
