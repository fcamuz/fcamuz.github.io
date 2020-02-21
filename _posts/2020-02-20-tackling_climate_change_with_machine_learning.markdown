---
layout: post
title:      "Tackling Climate Change with Machine Learning  "
date:       2020-02-21 01:23:39 +0000
permalink:  tackling_climate_change_with_machine_learning
---


Me and my data quest team-mates went for a Mindfire Global data challenge. And we are elevated to the next round of the selections to work on the project for C02 emmission reduction. 
During my research about this topic, I came accross this paper. Tackling Climate Change with Machine Learning. I wanted to summarize this paper so that me and my team-mates could skim this extensive study and get ideas of areas to implement machine learning to solve this issue.  

This paper aims to provide an overview of where machine learning can be applied with high impact in the
fight against climate change, through either effective engineering or innovative research. The paper is written for four group of people which are, researchers and engineers, entrepreneurs and investors, corporate leaders, local and national governments.  As data science community, we are ![](http://)natural party of this discussion. 


### Summary of "Tackling Climate Change with Machine Learning" 

https://arxiv.org/pdf/1906.05433.pdf

"Climate change is one of the greatest challenges facing humanity, and we, as machine learning experts, may wonder how we can help. Here we describe how machine learning can be a powerful tool in
reducing greenhouse gas emissions and helping society adapt to a changing climate. From smart grids
to disaster management, we identify high impact problems where existing gaps can be filled by machine
learning, in collaboration with other fields. Our recommendations encompass exciting research questions as well as promising business opportunities. We call on the machine learning community to join
the global effort against climate change" 


### 1- Electricity

ML can contribute on all fronts by informing the research, deployment, and operation of electricity
system technologies. Such contributions include accelerating the development of clean energy
technologies, improving forecasts of demand and clean energy, improving electricity system optimization
and management, and enhancing system monitoring. These contributions require a variety of ML paradigms
and techniques, as well as close collaborations with the electricity industry and other experts to integrate
insights from operations research, electrical engineering, physics, chemistry, the social sciences, and other
fields.

### 2- Transportation

While many of us probably think of autonomous vehicles and ride-sharing when we think of transport and ML, these technologies have
uncertain impacts on GHG emissions, potentially even increasing them. We discuss these disruptive
technologies in but show that ML can play a role for decarbonizing transportation that goes much
further. ML can improve vehicle engineering, enable intelligent infrastructure, and provide policy-relevant
information. Many interventions that reduce GHG emissions in the transportation sector require changes in
planning, maintenance, and operations of transportation systems, even though the GHG reduction potential
of those measures might not be immediately apparent. ML can help in implementing such interventions, for
example by providing better demand forecasts. Typically, ML strategies are most effective in tandem with
strong public policies. While we do not cover all ML applications in the transportation sector, we aim to
include those areas that can conceivably reduce GHG emissions.

Decarbonizing transport is essential to a low-carbon society, and there are numerous applications where ML
can make an impact. This is because transportation causes a large share of GHG emissions, but reducing
them has been slow and complex. Solutions are likely very technical, are highly dependent on existing
infrastructure, and require detailed understanding of passengers’ and freight companies’ behavior. ML can
help decarbonize transportation by providing data, gaining knowledge from data, planning, and automation.
Moreover, ML is fundamental to shared mobility, AVs, EVs, and smart public transit, which, with the right
incentives, can be used to enable significant reductions in GHG emissions.

### 3- Buildings&Cities

Machine learning provides critical tools for supporting both building managers and policy makers in
their efforts to reduce GHG emissions. At the level of building management, ML can help select
strategies that are tailored to individual buildings, and can also contribute to implementing those strategies
via smart control systems. At the level of urban planning, ML can be used to gather and make sense
of data to inform policy makers. Finally, we consider how ML can help cities as a whole to transition
to low-carbon futures.

A central challenge in this sector is the availability of high-quality data for training the algorithms, which
rarely go beyond main cities or represent the full spectrum of building types. Techniques for obtaining these
data, however, can themselves be an important application for ML (e.g. via computer vision algorithms to
parse satellite imagery). Realizing the potential of data-driven urban infrastructure can advance mitigation
goals while improving the well-being of citizens.


### 4- Industry

ML can potentially reduce global emissions by helping to streamline supply chains,
improve production quality, predict machine breakdowns, optimize heating and cooling systems, and prioritize the use of clean electricity over fossil fuels. However, it is worth noting that greater efficiency
may increase the production of goods and thus GHG emissions (via the Jevons paradox) unless industrial
actors have sufficient incentives to reduce overall emissions.

Given the globalized nature of international trade and the urgency of climate change, decarbonizing the
industrial sector must become a key priority for both policy makers and factory owners worldwide. As we
have seen, there are a number of highly impactful applications where ML can help reduce GHG emissions
in industry, with several caveats. First, incentives for cleaner production and distribution are not always
aligned with reduced costs, though policies can play a role in aligning these incentives. Second, despite the
proliferation of industrial data, much of the information is proprietary, low-quality, or very specific to individual machines or processes; practitioners estimate that 60-70% of industrial data goes unused.
Before investing in extensive ML research, researchers should be sure that they will be able to eventually
access and clean any data needed for their algorithms. Finally, misjudgments can be very costly for manufacturers and retailers, leading most managers to adopt risk-averse strategies towards relatively untested
technologies such as ML . For this reason, ML algorithms that determine industrial activities should
be robust enough to guarantee both performance and safety, along with providing both interpretable and
reproducible results.

### 5- Farms & Forests

ML can help monitor the health of forests and peatlands, predict the risk of
fire, and contribute to sustainable forestry. These areas represent highly impactful applications, in
particular, of sophisticated computer vision tools, though care must be taken in some cases to avoid negative
consequences via the Jevons paradox.

Farms and forests make up a large portion of global GHG emissions, but reducing these emissions is challenging. The scope of the problem is highly globalized, but the necessary actions are highly localized. Many
applications also involve a diversity of stakeholders. Agriculture, for example, involves a complex mix of
large-scale farming interests, small-scale farmers, agricultural equipment manufacturers, and chemical companies. Each stakeholder has different interests, and each often has access to a different portion of the data
that would be useful for impactful ML applications. Interfacing between these different stakeholders is a
practical challenge for meaningful work in this area.

### 6- Carbon Dioxide Removal 

Given limits on how much more CO2 humanity can safely emit and the difficulties associated with eliminating emissions entirely, CO2 removal may have a critical role to play in tackling climate change. Promising applications for ML in CO2 removal include informing research and development of novel component
materials, characterizing geologic resource availability, and monitoring underground CO2 in sequestration
facilities. Although many of these applications are speculative, the industry is growing, which will create
more data and more opportunities for ML approaches to help.

**Adaptation**
## 7- Climate Prediction

Recent trends have created opportunities for ML to advance the state-of-the-art in climate prediction. First, new and cheaper satellites are creating petabytes of climate observation data. Second, massive climate modeling projects are generating petabytes of simulated climate data. Third, climate forecasts
are computationally expensive (the simulations in took three weeks to run on NCAR supercomputers), while ML methods are becoming increasingly fast to train and run, especially on next-generation
computing hardware. As a result, climate scientists have recently begun to explore ML techniques, and are
starting to team up with computer scientists to build new and exciting applications.


ML may change the way that scientific modeling is done. Many components of large climate models can be replaced with ML models at lower computational costs. From an ML standpoint, learning from an existing model has many advantages: modelers can generate new training and test data on-demand, and the new ML model inherits some community trust from the old one. This is an area of active ML research. Recent papers have explored data-efficient techniques for learning dynamical systems, including physics-informed neural networks [508] and neural ordinary differential equations. In the further future, researchers are developing ML approaches for a wide range of scientific modeling challenges, including crash prediction, adaptive numerical meshing, uncertainty
quantification and performance optimization. If these strategies are effective, they may
solve some of the largest structural challenges facing current climate models.
New ML models for climate will be most successful if they are closely integrated into existing scientific
models. This has been emphasized, again and again, by authors who have laid future paths for artificial
intelligence within climate science. New models need to leverage existing
knowledge to make good predictions with limited data. In ten years, we will have more satellite data, more
interpretable ML techniques, hopefully more trust from the scientific community, and possibly a new climate
model written in Julia. For now, however, ML models must be creatively designed to work within existing
climate models. The best of these models are likely to be built by close-knit teams including both climate
and computational scientists.

### 8- Societal Impacts

Climate change will have profound effects on the planet, and the ML community can support efforts to
minimize the damage it does to ecosystems and the harm it inflicts on people. This section has suggested
areas of research that may help societies adapt more effectively to these ever changing realities. We have
identified a few recurring themes, but also emphasized the role of understanding domain-specific needs. The
use of ML to support societal resilience would be a noble goal at any time, but the need for tangible progress
towards it may never have been so urgent as it is today, in the face of the wide-reaching consequences of
climate change.

### 9- Solar Geoengineering

Any consideration of solar geoengineering raises many moral questions. It may help certain regions at
the expense of others, introduce risks like termination shock, and serve as a “moral hazard”: widespread
awareness of its very possibility may undermine mainstream efforts to cut emissions. Because of
these issues, there has been significant debate about whether it is ethically responsible to research this topic. However, although it creates new risks, solar geoengineering could actually be a moderating force against the terrifying uncertainties climate change already introduces, and ultimately
many environmental groups and governmental bodies have come down on the side of supporting further research. In this section, we have attempted to outline some of the technical challenges in implementing and evaluating solar geoengineering. We hope the ML community can help geoengineering researchers
tackle these challenges.

**Tools for Action**

### 10- Individual Action

While individuals can sometimes feel that their contributions to climate change are dwarfed by other factors,
in reality individual actions can have a significant impact in mitigating climate change. ML can aid this
process by empowering consumers to understand which of their behaviors lead to the highest emissions,
automatically scheduling energy consumption, and providing insights into how to facilitate behavior change.

### 11- Collective Decisions

The complexity, scale, and fundamental uncertainty inherent in the problems of climate change can pose
challenges for collective decision-making. ML can help supplement existing mathematical frameworks that
are employed to alleviate some of these challenges, including agent-based models, integrated assessment
models, multi-objective optimization, and market design. Interpretable and fair ML techniques may be of
particular importance in this context, as they may enable decision-makers to more effectively and equitably
employ insights from ML models. While these quantitative assessment tools can provide useful input to
the decision-making process, it is worth noting that decisions regarding climate change may ultimately
depend on qualitative discussions around norms, values, or equity considerations that may not be captured
in quantitative models.

### 12- Education 

Research has shown that educational activities centered on climate change and carbon footprints can engage learners in understanding the connection between personal and collective actions and their impact on
For further background on this area, see.
global climate, and can enable individuals to make climate-friendly lifestyle choices such as reducing energy use. There have also been proposals for interactive websites explaining climate science as well
as educational interventions focusing on local and actionable aspects of sustainable development. In
these contexts, ML can help create personalized educational tools, for instance by generating images of
future impacts of extreme weather events based on a learner’s address or by anchoring an individual’s
learning experience in a digital replica of their real-life location and allowing them to explore the way that
climate change will impact a specific location.


For those who want to apply ML to climate change, we provide a roadmap:

• **Learn.**  Identify how your skills may be useful – we hope this paper is a starting point.
• **Collaborate.**  Find collaborators, who may be researchers, entrepreneurs, established companies, or
policy makers. Every domain discussed here has experts who understand its opportunities and pitfalls,
even if they do not necessarily understand ML.
• **Listen.**  Listen to what your collaborators and other stakeholders say is needed. Groundbreaking
technologies have an impact, but so do well-constructed solutions to mundane problems.
• **Deploy.**  Ensure that your work is deployed where its impact can be realized.
We call upon the machine learning community to use its skills as part of the global effort against climate
change.





