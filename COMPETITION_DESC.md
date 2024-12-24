# COMPETITION DESCRIPTION

## Overview

We’re excited to announce a Deep Funding Christmas special: a **contest** to create a distilled human judgment mechanism predicting the relative importance of open source dependencies.

**Available**: 3,410 comparisons between 245 repos, one part provided for training & another for testing.

**Wanted**: Make 9.3 million predictions comparing 4,303 Ethereum repos and their dependencies with one another (includes consensus clients, developer tools and languages).

**Glory**: Your winning model can allocate $170,000 to open source contributors based on its predicted weights!

**Rewards**: An additional $80,000 for interesting open source submissions and valuable datasets or infrastructure useful to contest participants.

Funding for this competition is provided by Vitalik Buterin, the architect behind [deep funding](https://www.youtube.com/watch?v=ygaEBHYllPU).

# TL;DR

- Build a model to predict funding weights for 9.3 million comparisons among 4,303 Ethereum open source repos based on past funding data showing 3410 comparisons across 245 repos.

- Submissions are tested using 1,023 out of the 3,410 comparisons. Do not overfit your model: this is a weakly supervised machine learning contest since a proxy dataset is provided for training. Winners are ultimately chosen through data collected from the relevant open source maintainers and other jury members from now until the end of the competition.

- You are encouraged to be creative in the datasets used for your models beyond what is provided and incentivized to share them with other contestants. Please ensure your model outputs are logically consistent and do not contain transitivity violations, ie c/a = c/b \* b/a. For example, if a is weighed less than b and b is less then c, your model should not have an output where a is weighed more than c.

- Winning model gets to allocate $170,000 of funding based on the weights it predicts for the 4,303 repos.

- A total of $80,000 in prizes to open source submission of winning models & other infrastructure that is valuable to other contestants and designers of the mechanism.

- Results declared on February 27 2025.

## What is Deep Funding?

[Deep Funding](https://deepfunding.org) has 3 components:

1. An [unweighted dependency graph](https://cosmograph.app/run/?data=https://raw.githubusercontent.com/opensource-observer/insights/refs/heads/main/community/deep_funder/data/unweighted_graph.csv&source=seed_repo_name&target=package_repo_name&gravity=0.25&repulsion=1&repulsionTheta=1&linkSpring=1&linkDistance=10&friction=0.1&renderLabels=true&renderHoveredLabel=true&renderLinks=true&linkArrows=true&curvedLinks=true&nodeSizeScale=0.5&linkWidthScale=1&linkArrowsSizeScale=1&nodeSize=size-default&nodeColor=color-outgoing%20links&linkWidth=width-number%20of%20data%20records&linkColor=color-number%20of%20data%20records&) showing all the contributions making up a valuable project.

2. A plurality of deep learning model submissions giving weights to the relative value between contributions.

3. A human judgment mechanism making manual comparisons between a subset of the contributions, for the purpose of choosing a winning model most closely aligned with their preferences that then gets to allocate funding based on its proposed weightages.

## Why Deep Funding?

- To support ALL relevant dependencies, not just those who make an application in time to a particular funding round.

- To remove the need for extensive public campaigning or currying favor with decision makers to receive funding.

- To be able to run more frequent funding rounds many projects by creating an approximate copy of costly mechanisms that are hard to operate at a high cadence for a large number of eligible projects.

## How the Contest Works

- **Datasets**: Participants are given

[Funding data](https://github.com/deepfunding/dependency-graph/issues/13) from Open Collective, Gitcoin, and Optimism retroactive rounds for repositories that participated in the same rounds.

This dataset takes the form of relative comparisons between 245 repos based on decisions made by actual funders, yielding 3,410 comparisons.

Example: walletconnect-monorepo vs ethers.js gives a relative weight of 0.33171687205 vs 0.66828312795 respectively (values must add up to one). This data was calculated based on funding rounds where ethers.js received twice the amount of funding of wallet-connect monorepo.

Submission data comprising a list of 4,303 open source repos supporting Ethereum , chosen from [clientdiversity.org](https://clientdiversity.org) & [github.com/ethereum](https://github.com/ethereum) (level 1) and their dependencies (level 2).

You need to compare each of these repos with one another (9.3 million comparisons) and give a relative value between them, such that the total in each case adds up to 1 (up to 11 decimal points).

Example: eth-abi and eth-account do not appear in the funding data provided. Based on training data, please give a relative weight to each such that they add up to one.

- **Challenge**: Build a model that predicts 9.3 million comparisons between any 2 repos from the entire dataset of 4,303 repos.

The funding dataset will let you approximate how much funding all relevant repositories would have received if they had taken part in funding rounds. However, your goal is predicting each repo’s relative importance based on how open source maintainers and a jury would rank them.

- **Winner**

70% of the 3,410 comparisons made available to participants as training data.

30% for testing model submissions.

However, do not overfit your model: ultimate winners are decided based on data currently being collected from open source maintainers comparing their dependencies against one another.

Answers given by the model must be self-consistent, ie. for any triple a,b,c, c/a = c/b \* b/a. So do NOT just rely on inconsistent funding data provided and let the predictions run. Please ensure mathematical consistency in outputs given to reflect logical relationships rather than reflecting biases from the training data.

Results will be made public on February 27 2025.

May the best model(s) win!

## Why Join the Challenge?

1. **Advance funding mechanisms**: Help shape the future of public goods funding by improving how we allocate resources to underfunded dependencies.

2. **Recognition**: Gain visibility in the open-source and Web3 communities for your innovative approaches.

3. **Win Prizes**: The chance to win prizes and allocate funding from Vitalik Buterin based on how good the judgments made by your model are.

## Timeline

- **December 24 2024**: Contest opens.
- **February 20 2025 at 11:59:59 AoE time**: Submision deadline.
- **February 27 2025**: Results announcement.

## Resources

- Sign up via HuggingFace.
- Join the community discussion and ask questions in our [Telegram group](https://t.me/AgentAllocators)
- Look at the Deep Funding [GitHub repo](https://github.com/deepfunding)
- [Hear](https://www.youtube.com/watch?v=ygaEBHYllPU) the podcast with Vitalik Buterin on this new mechanism.
- [Description](https://github.com/deepfunding/dependency-graph/issues/13) of the proxy dataset.
- Deep Funding [website](https://deepfunding.org).
