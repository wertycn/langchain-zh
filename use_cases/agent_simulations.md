# 代理模拟

代理模拟涉及通过相互交互来实现一个或多个代理的模拟。
代理模拟通常包括两个主要组成部分：

- 长期记忆
- 模拟环境

代理模拟的具体实现（或代理模拟的某些部分）包括：

## 单代理模拟
- [模拟环境：Gymnasium](agent_simulations/gymnasium.ipynb)：使用[Gymnasium](https://gymnasium.farama.org/)（前身为[OpenAI Gym](https://github.com/openai/gym)）创建一个简单的代理-环境交互循环的示例。

## 双代理模拟
- [CAMEL](agent_simulations/camel_role_playing.ipynb)：实现CAMEL（通信代理，用于“Mind”探索大规模语言模型社会）论文的代码，在这篇论文中有两个代理之间的交流。
- [双人D&D](agent_simulations/two_player_dnd.ipynb)：使用通用的双代理模拟器实现流行的龙与地下城角色扮演游戏（Dungeons & Dragons）的变种的示例。
- [代理人使用工具进行辩论](agent_simulations/two_agent_debate_tools.ipynb)：演示如何让对话代理人使用工具来辅助生成回复。

## 多代理人模拟
- [多人D&D](agent_simulations/multi_player_dnd.ipynb)：演示如何使用通用对话模拟器为多个对话代理人提供支持，并使用自定义讲话次序来展示一种流行的角色扮演游戏“龙与地下城”的变种。
- [分散式演讲者选择](agent_simulations/multiagent_bidding.ipynb)：演示如何实现多代理人对话，而不需要固定的发言安排，而是让代理人通过竞价来决定谁应该发言。该示例展示了如何在虚构的总统辩论背景下实现该功能。
- [独裁演讲者选取](agent_simulations/multiagent_authoritarian.ipynb): 这是实现多代理对话的示例，其中一个特权代理定向决定每个人说什么。 此示例还演示了如何使特权代理确定对话何时终止。 这个示例是在虚构新闻展示的背景下展示的。
- [模拟环境：PettingZoo](agent_simulations/petting_zoo.ipynb): 这是一个使用[PettingZoo](https://pettingzoo.farama.org/)（[Gymnasium](https://gymnasium.farama.org/) 的多代理版本）为多个代理创建代理环境交互循环的示例。
- [生成代理](agent_simulations/characters.ipynb): 本笔记本实现了基于论文[生成代理：人类行为的交互式"模拟"]（https://arxiv.org/abs/2304.03442）的作品中的生成代理，作者是Park等人。