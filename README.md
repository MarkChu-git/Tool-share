# Tool-share
# 工具整理

## 目录

[toc]

## GenAI篇

### 排名

#### 权威媒体

![image-20250206174910504](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250206174910504.png)

### 个人看法

#### 前言

在用过所有的语言大模型（下文简称GenAI或LLMs）之中，很难用一句话概括哪一个模型好用，哪一个模型不好用，因为每一家公司、每一个LLM都**各有特点，没有极致的好也没有极致的烂**。例如Openai的ChatGPT无论是长文本生成还是逻辑推理都毫无疑问处于第一梯队，但是o1配额非常少，由于巨大的访问量，GPT4o和GPT4(legacy)很多时候不得不面对降智等问题；幻方的DeepSeek各方面也十分出色，以极其低廉的训练成本而闻名，但由于是免费在线提问，加之大洋彼岸的国家级ddos攻击，使得访问非常不稳定。

所以，首先要说，对于GenAI的使用，都是**取其精华，去其糟粕**的过程，合理运用每一个LLMs才更有助于发展。

#### 深度对比

从我个人的使用体验和生成质量，可以粗略的排一下名：

- T0: Claude 3.5 Sonnet, DeepSeek R1, ChatGPT o1, Gemini Advanced 2.0 Pro Experimental
- T1: GPT o3-mini-high, GPT 4o, GPT 4(legacy), DeepSeek V3, Claude 3.5 Sonnet(June), 豆包
- T1.5: GPT 4(legacy), Claude 3.5 Haiku
- T2: Claude 3 opus, GPT 4o-mini, Gemini 1.5, Gemini 2.0 

其他LLM暂时不做讨论（没用过或者场景不适用），下面展开讨论一下各个模型之间的使用感受。

#### 使用感受

总结目前我的使用场景，一共分为**逻辑推理与演绎，数学运算，编程能力，自然语言生成**四个方面。真正将模型之间拉开差距的是**数学能力与自然语言生成**。这一部分内容相对来讲会比较笼统，后文会详细的各个模型之间的感受。

##### 逻辑推理与演绎

逻辑推理和演绎能力是指大模型在面对复杂的推理任务时，是否能够从给定的前提中推导出合理的结论。

实际体验下来，Claude 3.5 Sonnet和DeepSeek R1逻辑推理能力最强，o1紧随其后，与前两者平分秋色。T1和T1.5方阵也表现不俗，足以胜任日常学习的需求。T2有所欠缺，推理中偶尔仍可能出现错误，尤其是当推理链条过长或问题非常复杂时，但是也可以应付大部分场景。

##### 数学运算

在陈述各个LLMs之间数学运算能力差别之前，先要给大家讲解一下为什么大模型数学运算能力比较弱：

1. **训练数据的性质**

- 大语言模型主要基于**文本数据训练**,而数学推理需要的是**严格的逻辑和符号运算能力**
- 文本中的数学内容往往是描述性的,缺乏实际的运算过程
- 数学推理中的抽象概念和符号操作难以完全通过自然语言表达

2. **模型架构的限制**

- Transformer架构擅长**处理序列和模式识别**,**但不是专门为数学运算设计的**
- 缺乏显式的数学运算模块,所有计算都需要通过**注意力机制**间接完成
- 对于精确的数值计算,容易出现累积误差

3. **推理链路的不确定性**

- 数学推理要求每一步都严格准确,而语言模型的输出本质上是**概率分布**
- 复杂数学问题需要多步推理,错误可能在任何步骤产生并传播
- 模型难以像人类那样进行**回溯和纠错**

不理解？那我们用更通俗的话讲一讲

想象一下,大语言模型就像一个"**超级模仿者"** - 它通过学习大量的文本来理解和生成内容。就像一个人通过看别人做菜的视频学习烹饪一样,模型是通过**"看"**大量文本来学习的（通过**自监督学习**在大规模语料库上训练来获取**文本表征和生成能力**）。

这种学习方式在处理语言方面很有效,因为语言中有很多可以直接模仿的模式。比如看到"你好"后面经常跟着"请问",模型就能学会这种对话模式。

但是数学计算和推理不太一样:

1. **数学需要精确运算** 比如说 1234 × 5678 这样的运算,模型只是"看到过"类似的题目和答案,但并没有真正理解乘法的运算过程。这就像你看过很多人打篮球,但并不意味着你自己就会投篮一样。
2. **推理需要严密的逻辑** 解决数学问题常常需要多个步骤的推理。模型可能知道每个步骤"看起来"应该是什么样子,但不一定能准确地连接这些步骤。这就像背台词和真正理解剧情是两回事（缺乏处理抽象符号系统的机制来保证推理的完整性和正确性）。
3. **缺乏"运算能力"** 模型本质上是在处理文本,没有像计算器那样的专门运算部件。它更像是在通过记忆和模仿来"猜"答案,而不是真正地"算"出来。

这就是为什么当我们需要进行精确的数学计算时,往往需要**借助专门的计算工具来辅助大语言模型,而不是完全依赖它的输出**。

所以在测试中，能明显看出，T0方阵在解答数学题方面远超其他模型。Claude 3.5 Sonnet本身自带Analysis Tool，o1和DeepSeek R1都是强大的**推理模型**，数学能力明显更强。T1方阵虽然能解决绝大部分数学题，但是发生输出内容错误的概率高于T0，解决大部分数学题可以，稍微难一些的题便很难招架得住。T2并不适合做数学运算，这里不过多赘述。

结合我自己的实践和经验，实际体验中Claude 3.5 Sonnet和DeepSeek的使用中，无论是性价比（o1配额少）还是生成准度**均略高于**o1。在实际解题之中，通识类的数学课，T1.5、T1以上基本都可以解决，非常复杂的数学问题才需要调用T0。

在实际解题时，最好采用直接输入**LaTex公式**的方式来进行提问，相较于拍摄图片或截屏，解题效率和准度都要高不少。

**E.g.**

![image-20250207001506999](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207001506999.png)

Evaluate the indefinite integral: \int{(3x^2-4x+5)}dx (most recommended)

##### 编程能力

同上述两个方面，Claude 3.5 Sonnet和DeepSeek R1编程能力最强，o1紧随其后。T1和T1.5方阵能够胜任打分日常学习的需求，但bug较多。T2非常欠缺，编程中大概率出现错误，尤其是问题非常复杂时。

这里我们采用**对照实验**和**控制变量法**，唯一变量是**LLMs**，提示词（Prompts, 下文同）、提问方式保持一致。

Prompt：编写一段javascript代码，显示一个球在旋转的六边形内弹跳，球会受到重力、摩擦力的影响，并且它必须真实的从旋转的墙壁上反弹，用javascript和html实现它。

###### 实验结果

**Claude 3.5 Sonnet：**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207002507777.png" alt="image-20250207002507777" style="zoom:33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207002534686.png" alt="image-20250207002534686" style="zoom:33%;" />

（非常出色，和DeepSeek R1只有旋转速度的区别，物理模型都是正确的）

**DeepSeek R1:**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207002616414.png" alt="image-20250207002616414" style="zoom: 33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207002653692.png" alt="image-20250207002653692" style="zoom:33%;" />

（自家孩子没丢脸，表现非常出色）

**DeepSeek V3:**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207003610456.png" alt="image-20250207003610456" style="zoom:33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207003640087.png" alt="image-20250207003640087" style="zoom:33%;" />

（虽然有所失误但强于ChatGPT）

**ChatGPT o1:**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207002825323.png" alt="image-20250207002825323" style="zoom:33%;" />

（跑起来的时候给我笑飞了）

**ChatGPT 4o:**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207002945183.png" alt="image-20250207002945183" style="zoom:33%;" />

（这什么东西？）

**ChatGPT 4：**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207004035483.png" alt="image-20250207004035483" style="zoom:33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207004120683.png" alt="image-20250207004120683" style="zoom:33%;" />

（出乎意料，明显强于4o和o1，略弱于DeepSeek V3）

**豆包：**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207004715018.png" alt="image-20250207004715018" style="zoom:33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207004754513.png" alt="image-20250207004754513" style="zoom:33%;" />

（小球动一下，直接掉出去了，我猜是碰撞处理函数 `handleCollision` 过于简单）

**Claude 3.5 Haiku**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207005057162.png" alt="image-20250207005057162" style="zoom:33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207005154521.png" alt="image-20250207005154521" style="zoom:33%;" />

（出乎意料，非常棒，完全不弱于DeepSeek R1和Claude 3.5 Sonnet，是所有测试模型中响应和生成速度最快的）

**ChatGPT 4o mini:**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207005821747.png" alt="image-20250207005821747" style="zoom: 33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207005913679.png" alt="image-20250207005913679" style="zoom:33%;" />

（最出乎意料，效果远远好于o1和4o）

**Gemini 2.0 Pro Experimental:**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207162454312.png" alt="image-20250207162454312" style="zoom:33%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250207162514065.png" alt="image-20250207162514065" style="zoom:33%;" />

（非常出色，是所有推理模型之中响应最快的）

主流模型到这里就测试完毕了。通过本场实验，虽然能看出大模型之间编程能力的区别，但是编程能力的考察是**非常复杂且非常多样的，难以从单一测试中反馈出所有问题**。在实际使用中，不仅要参考本场实验的结果，还要结合具体的使用场景，例如豆包的Marscode可以集成在Cursor和VS Code实现**代码补全功能**；各个模型的API服务也可以接入VS code，实现代码生成……

##### 自然语言生成

相信大家一定最为关心这一部分的内容，因为这一场景在现实生活使用中最为频繁。因此这一部分主要从我**个人的经验**出发，不谈论过多的技术，就LLMs的**生成质量**等方面进行讨论。

**对于LLMs来说，自然语言生成是其最擅长的事情**。其实不难发现，T0方阵除Claude 3.5 Sonnet以外所有的模型，都被定义成推理模型（reasoner)。推理模型最擅长的工作是**数据分析、代码生成，数学运算和逻辑推理**，虽然推理模型也有很强的自然语言生成能力，但如果只是用它去生成简单的文本，那可以说是暴殄天物，尤其是ChatGPT o1。所以这里**并不是非常建议采用推理模型去生成长文本**，T1和T1.5本身就有着很强的文本输出能力且大部分情况完全够用。只要遇到非常难以处理的文本或问题，才建议去调用推理模型。

自然语言生成质量也遵循先前的排名。但从个人经验角度来讲，**Claude 3.5 Sonnet**和**ChatGPT 4o**的自然语言生成质量很高， 尤其是**Claude 3.5 Sonnet**，生成内容更加贴近人类写作，AI率（见下文）比起其他模型也相对较低；**ChatGPT 4o**长文本生成能力也很优秀，其优势主要在于，4o可以实时联网，并且前端功能丰富（联网、生成图片、Canvas、GPTs），可以调用一些专门训练的GPT进行写作或查找文献；**DeepSeek R1和V3**的自然语言生成质量也很高，联网功能不仅能够搜索中文网站，也能够搜索外文网站；**豆包**自然语言生成质量也很高，面板前端功能丰富，免费且高质量让其十分耀眼。**中文内容生成**上，**DeepSeek、豆包等国产模型**生成质量较高于**Claude 3.5 Sonnet**和**ChatGPT 4o**。反之，**Claude 3.5 Sonnet**和**ChatGPT 4o**则明显更胜一筹。不过在实际体验中，因为所有LLMs的训练过程中英文语料库都很丰富，且各个模型之间都会**相互蒸馏**，所以实际体验上感知并不明显，使用中取长补短即可。

但这些模型也并不是没有缺点的。上文提到，语言模型的输出本质上是**概率分布**，这就意味着大模型在生成内容时，犯错是经常的事，甚至很多是事实性的错误。从个人经验角度来讲，譬如让GPT推荐相关文献时，时常出现**编造不存在的文献**的情况，Claude 3.5 Sonnet本身无法联网，可能存在知识库内容不够丰富的情况。

不过，这些问题也并非完全无法避免：

1. 大模型在生成内容是**调用自己现有的知识库**再依照**概率分布**进行生成，我们可以通过**增强提示词工程**来使回答变得专业，Github、YouTube、B站、小红书甚至是Reddit和知乎上有很多模板可以直接调用。
   1. 推荐课程：
      1. 吴恩达教你写Prompts：https://learn.deeplearning.ai/courses/chatgpt-prompt-eng/lesson/1/introduction（中文熟肉（更建议英文原版））：https://www.bilibili.com/video/BV1Z14y1Z7LJ/?spm_id_from=333.337.search-card.all.click&vd_source=8890a3611d7384244a0a07ffef8d2fd7）
      2. Prompts Engineering-OpenAI（OpenAI官方推出的手册）：https://platform.openai.com/docs/guides/prompt-engineering
      3. Github优秀的Prompts分享项目
         1. https://github.com/eseckel/ai-for-grant-writing
         2. https://github.com/f/awesome-chatgpt-prompts
         3. https://github.com/ai-boost/awesome-prompts/tree/main
         4. https://github.com/langgptai/wonderful-prompts
2. 大模型的生成并不是仅仅靠Prompts，还有靠用户“投喂”资料，将自己现有的文献直接为给大模型（不需要反复投喂，市面上现有大模型**都能看到上下文**。）

**最重要的一点，道高一尺魔高一丈，目前没有任何一个大模型可以完全通过AI率测试（识别为人类文本）**

#### 详细使用感受

##### Claude 3.5 Sonnet

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208172835053.png" alt="image-20250208172835053" style="zoom: 50%;" />

Claude 3.5 Sonnet是我**目前使用下来体验感最好的大模型**，几乎很少有降智的情况，在各方面全面开花，是我目前的主力之一。Claude 3.5 Sonnet是所有模型之中最贴近的人类文本的（AI率检测都是100%，但是文本在后期进行优化要省不少劲）。此外**编程能力和数学运算**也是非常强悍。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208173119339.png" alt="image-20250208173119339" style="zoom:50%;" />

Claude虽然前端面板的功能没有ChatGPT和豆包那样丰富，但是也有类似与GPTs的功能（如上图）——**Projects**，可以创建属于自己的AI。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208173839122.png" alt="image-20250208173839122" style="zoom: 33%;" />

Claude的其中一个优势在于，如果是编程，Claude可以进行实时运行和渲染来展示项目，互动性很强。

但Claude也并非完美无瑕，首先，Claude虽然是多模态模型，但并不如豆包、ChatGPT那般功能丰富。Claude**无法生成图片也无法生成音频**。Claude 3.5 Sonnet就算在Professional Plan配额也并不是很多，并且**风控极高，被封号的可能性大**。不过，瑕不掩瑜，常用的功能一个也不少。

###### 总结

优点

- Claude 3.5 Sonnet在处理复杂任务时表现出色,尤其在需要深度分析和逻辑推理的场景中。它能够理解复杂的上下文,并提供连贯且深入的解答,这使它特别适合处理专业领域的问题和学术讨论。
- 模型展现出很强的多语言理解和生成能力。它不仅能准确理解各种语言的细微差别,还能用地道的表达方式回应,在中文交流中也能保持自然流畅的对话风格。
- 在编程和技术支持方面表现突出,能够编写高质量的代码,提供详细的技术文档,并帮助调试和优化现有代码。它对多种编程语言都有很好的掌握,并能理解不同编程范式。
- 在创意写作和内容创作方面具有很强的能力,能够生成各种风格的文章、故事和其他创意内容。它能理解并模仿不同的写作风格,保持内容的连贯性和原创性。

缺点

- 虽然模型能力强大,但在处理实时数据和最新信息时存在局限性。**它的知识库有截止日期**,这意味着它可能无法提供最新的信息和发展动态。
- 前端面板的功能不够丰富，不能像GPT一样实现多种多样的功能，不能输出图片、视频和音频。
- 尽管具备创造力,但在需要极具创新性或打破常规思维的任务中,可能仍然会表现出一定的局限性。它的输出可能会倾向于更常规和安全的方案。

##### ChatGPT 4o

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208180024997.png" alt="image-20250208180024997" style="zoom: 33%;" />

没有人会对ChatGPT陌生，除非断了网。

ChatGPT 4o虽然已经跌落神坛，但不可否认，其仍然是现在最先进的模型之一。图片生成、逻辑推理、数学运算样样在行，优点不过多赘述。

真正需要注意的是它的**缺点**。因为ChatGPT 4o等OpenAI其他模型访问量极大，所有模型都会时不时出现**拉高风控和降智的情况**，这种感受是很容易察觉出来的。

解决办法也正是GPT的优势——**GPTs**

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208181052138.png" alt="image-20250208181052138" style="zoom: 50%;" />

我们可以通过特定提示词来训练我们想要的GPT，实现功能的细化，最重要的是GPTs商店有很多**高质量的GPTs**。需要注意的是，某一些GPTs会调用外部接口，可能会要求付费， 大家依照自己的需求，**谨慎氪金**（不是所有都值得花钱的，免费的GPTs够用）。

**GPTs推荐:**



<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208181443716.png" alt="image-20250208181443716" style="zoom:50%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208181601137.png" alt="image-20250208181601137" style="zoom: 50%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208181643362.png" alt="image-20250208181643362" style="zoom: 50%;" />

<center style>(Universal Primer是GPTs中最大的功臣，期末的时候帮我解释了很多复杂的知识，强烈推荐)

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208181816862.png" alt="image-20250208181816862" style="zoom:50%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208181858659.png" alt="image-20250208181858659" style="zoom:50%;" />

<center style>这些GPTs都是经过精校过的4o或4，能够大幅改善GPT降智的情况

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208225009873.png" alt="image-20250208225009873" style="zoom: 67%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208225810919.png" alt="image-20250208225810919" style="zoom: 67%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208231514080.png" alt="image-20250208231514080" style="zoom:50%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208231537021.png" alt="image-20250208231537021" style="zoom:50%;" />

Github项目推荐：https://github.com/ai-boost/Awesome-GPTs?tab=readme-ov-file

##### DeepSeek

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208231841675.png" alt="image-20250208231841675" style="zoom: 50%;" />

![image-20250208231811965](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208231811965.png)

最近一段时间DeepSeek的爆火让全世界认识到“美国人能造出来，中国人不比他们少个脑子。”作为从2024年11月就开始体验DeepSeek V2.5的“老用户”来说，DeepSeek的爆火并不令人意外。很多人认为DeepSeek厉害的点在于是初创公司，首先这是完全错误的，DeepSeek的母公司正是**幻方**，是我国量化金融的巨头（说白了不缺钱），实际上真正令人感到吃惊的是这家企业居然可以用如此之小的成本办出这么大的事儿，以至于有从业者讲美国企业如果想要做出同等效果的模型花销最起码是**DeepSeek的30倍**以上。

|  比较项  |           DeepSeek            |          OpenAI          |
| :------: | :---------------------------: | :----------------------: |
| GPU数量  |    约 10000 张 NVIDIA H800    | 数万张 NVIDIA A100/H100  |
| 算力成本 |    功耗较低，计算效率较高     |   计算量庞大，能耗更高   |
| 经济成本 |  训练成本约**550-600万美元**  | 训练成本高达**数亿美元** |
| 模型架构 | 混合专家（MoE），部分参数激活 |  密集架构，所有参数激活  |
| 参数规模 |      6710亿（激活370亿）      |   1750亿+（全部激活）    |
| 推理效率 |  高效，按需激活参数，省资源   |  计算需求大，运行成本高  |

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208235523430.png" alt="image-20250208235523430" style="zoom: 33%;" />

从各方面能力来看，DeepSeek完全不输任何一款大模型。实际体验上，DeepSeek V3和R1也当之无愧属于第一梯队，联网搜索不仅能搜索国内网站，也能搜索国外网站。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250208234648026.png" alt="image-20250208234648026" style="zoom: 50%;" />

DeepSeek的缺点也很明显，现阶段的DeepSeek爆火导致**服务器资源紧张**，时常会出现“服务器繁忙，请稍后重试”，系统非常不稳定；DeepSeek目前的两个模型均为**单模态模型**，当输入照片的时候，其实对照片进行**OCR识别**，**图片转文字**后再输入，并且识别精度并不是很高，所以如果图片中**文字不清晰或者根本没有文字**，那便会出现**上传图片失败的情况**；能够同时输入的文件数量也要明显少于其他的模型。

就目前而言，DeepSeek更适合**长文本、代码生成和数学运算**，DeepSeek中加入多模态模型也只是**时间问题**。

DeepSeek现在有V3和R1两个模型，他们的调用逻辑如下：

###### 调用逻辑

- 无深度思考+无联网搜索=DeepSeek V3（知识库截至2024年7月）
- 无深度思考+联网搜索=DeepSeek V3（实时知识库）
- 深度思考+无联网搜索=DeepSeek R1（知识库截至2023年10月）
- 深度思考+联网搜索=DeepSeek R1（实时知识库，先搜索后推理）

###### 使用推荐

- 强推理+大量数据=深度思考+无联网搜索
- 强推理+大量实时数据=深度思考+联网搜索
- 大量文本处理和生成=无深度思考+无联网搜索
- 大量文本处理生成+实时数据=无深度思考+联网搜索

此外，截至2025年2月9日，DeepSeek API服务已恢复（服务器繁忙，已关闭充值功能，原有金额仍可以调用）。API服务可以集成在Cursor和VS Code实现代码补全和生成。对于没有编程需求的同学，API服务也并不和你完全无关，**沉浸式翻译（详见下文）**可以接入DeepSeek API实现AI翻译，效果远好于普通的机器翻译。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209001637926.png" alt="image-20250209001637926" style="zoom: 50%;" />

##### Gemini

Gemini这个部分本来是不想谈的，先前的Gemini 1.5在实际使用体验中非常糟糕，性价比极低。这篇文章写到一半时，才关注Gemini迎来了重大更新，相比之前，生成质量高了太多。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209001928306.png" alt="image-20250209001928306" style="zoom: 67%;" />

Gemini最大的优势并不在于高质量的内容生成，而是在于**和谷歌生态深度绑定**。Gemini可以实时读取Youtube视频，Google地图，Google搜索，如果用Gemini写邮件，可以通过Gmail发出，不需要复制。一句话，只要你有Google生态，你便可以体验Gemini的强大。**下面讲讲如何薅Gemini的羊毛**。

###### 薅羊毛（或许是最重要的部分）

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209002643507.png" alt="image-20250209002643507" style="zoom: 67%;" />

只有**Gemini Advanced**可以访问**2.0 Pro Experimental（推理模型）、1.5 Pro with Deep Research、1.5 Pro**

如图所示，Gemini Advanced有一个月的免费试用期，我们如何一直薅羊毛呢？通常Gmail注册**需要手机号码验证**，但如果**通过手机注册**便可以绕过这一环节（电脑无法绕过），只要Google不取消这一政策，便可以循环薅羊毛。我们可以通过绑定银行卡或者Touch n go的方式进行订阅，流程如下：

- 必须使用手机注册新的Gmail（不建议使用常用Gmail账号薅羊毛，开新账号最好）
- 登录后打开Gemini（iOS和Android都可以下载，Android在Google Play内下载，iOS改非中国大陆区；电脑用Chrome打开）
- 点击“试用Gemini Advanced”
- 点击“立即订阅”后，会弹出界面，Google Pay有绑定卡可以直接用卡，没有的如下图（以马来西亚为例，全世界大同小异，其他地区应为Paypal），马来西亚地区同学建议使用Touch n Go。不用担心，这一步骤不会扣费。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209003917494.png" alt="image-20250209003917494" style="zoom: 50%;" />

- 正常订阅完后，点击头像进入“管理Google账号”，再点击“付款和订阅”，如下图

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209004431363.png" alt="image-20250209004431363" style="zoom:50%;" />

- 点击“管理订阅”
- 里面可以直接取消订阅，一个月后**Gemini Advanced及其附带权益便会失效**，这个时候再如法炮制一个就好啦~

##### 豆包

豆包最大的优势是**前端面板功能非常丰富，可以实现多种多样的功能**，现阶段完全免费，而且生成质量高。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209004827191.png" alt="image-20250209004827191" style="zoom: 33%;" />

唯一值得关注的是，豆包有两个版本，**一个是大陆版的豆包，另一个是海外版的Cici**。两个都隶属于字节跳动，本质上是一款软件。

实际使用中， 在海外（中国大陆以外）豆包**响应速度并不稳定**，但Cici要明显好不少，响应速度更快；由于使用区域不同，豆包和Cici虽然服务器相同，但豆包的**风控更高**，**触发敏感词的概率高于Cici**。**Cici的更新较为滞后**，**前端面板功能不如豆包丰富**。如果豆包访问较好，可优先使用豆包，反之建议用Cici。一句话，大陆内用**豆包**，大陆外用Cici，具体情况具体分析。

------

### 实用工具篇

#### 前言

能看到这的朋友，感谢你们听我啰嗦，或许这才是你们最期待的部分。不过，如果没有前文的铺垫，恐怕这一部分也很难推进，虽然本篇名为“实用工具篇”，但是跟上文密切相关。我们熟知的Grammarly，Quillbot，AI Humanizer, GPTZero等工具，**本质上也是大模型**，他们是**经过特定使用场景优化的大模型**。另外，这一部分相对零碎，会分享我用过的所有实用工具。

#### AI Humanizer（人格化AI文本）

##### 前言：为什么AI detector能够检测出AI率

> ###### 一、AI生成文本的固有特征
>
> AI生成的文本（如GPT、Claude等模型的输出）虽然高度流畅，但存在以下可检测的特征：
>
> 1. **统计模式的一致性**
>    - AI生成的文本通常具有**较低困惑度（Perplexity**，说白了就是模型对数据的**“懵逼程度”**。数值越低，模型越“清醒”，预测越准；数值越高，模型越“困惑”，预测越不确定。），即模型更倾向于选择“高概率”的常见词汇和句式，导致文本过于平滑，缺乏人类写作中的随机性和多样性。
>    - 例如，AI可能过度使用某些连接词（如“此外”“然而”）或固定句式。
> 2. **结构规律性**
>    - 长文本中可能出现**重复的逻辑结构**（如段落开头总是总结句，后接解释），而人类写作更灵活。
>    - 句法复杂度较低，长句嵌套较少，标点使用更单一。
> 3. **语义与事实的局限性**
>    - AI生成的文本可能在细节上表现出**逻辑矛盾**或**事实错误**（尤其是需要专业知识的场景）。
>    - 对人类特有的经验描述（如个人感受、具体场景回忆）可能显得空洞或模板化。
> 4. **隐藏的“水印”特征**
>    - 部分AI模型（如GPT-3后期版本）会在生成文本中植入**不可见的统计标记**，通过特定算法可检测到这些标记。
>
> ------
>
> ###### 二、AI Detector的技术实现
>
> 检测器通过以下步骤识别AI生成文本：
>
> 1. **特征提取**
>
> - **词频与分布分析**：统计文本中词汇的分布（如Zipf定律偏差）、罕见词使用频率等。
> - **句法分析**：检测句子结构的复杂性和多样性（如依存句法树的深度）。
> - **语义连贯性**：通过预训练模型（如BERT）分析上下文逻辑是否过于“完美”，缺乏人类常见的跳跃或冗余。
>
> 2. **模型训练**
>
> - **监督学习**：使用标注好的AI生成文本（正样本）和人类文本（负样本）训练分类模型。
> - **常见模型**：
>   - **基于神经网络的分类器**：如微调的RoBERTa、DeBERTa。
>   - **统计模型**：通过困惑度、词频熵等指标构建阈值判断。
> - **对抗训练**：加入对抗样本提高模型鲁棒性（Robustness），防止被AI生成的优化文本绕过。
>
> 3. **实时检测**
>
> - 输入文本经特征提取后，模型输出为AI生成的概率值（如GPTZero显示的结果）。
> - 部分工具结合多维度分析（如写作风格突变检测）提高准确性。
>
> ------
>
> ###### 三、典型案例与工具
>
> 1. **GPTZero**
>    - 通过分析文本的**困惑度（Perplexity）和突发性（Burstiness）**（句子长度变化率）区分AI与人类写作。
>    - AI文本通常困惑度低且突发性低（句子长度更均匀）。
> 2. **OpenAI Text Classifier**
>    - 基于GPT系列模型的内部特征训练，检测生成文本的统计指纹。
> 3. **Turnitin AI Detection**
>    - 结合语法模式、引用风格等教育场景特征，专门针对学术写作优化。

---

> 没理解？那我们通俗的讲一讲。
>
> 1. **AI文本生成的规律性**
>
> AI生成的文本通常是基于大量的文本数据进行训练，生成的内容往往会有一些共同的特点。比如，它们可能会有重复的模式或句式结构，这种“规律性”是人类写作中不太常见的。AI生成的文本更倾向于使用常见的词汇和结构，而缺乏某些创新性或个性化的表达。因此，AI检测器可以通过分析这些模式，判断文本是否来自AI。
>
> 2. **语法与风格**
>
> AI生成的文本在语法上通常比较规范，但可能缺乏一些细微的表达差异。例如，AI可能在某些句子的结构上过于简洁，缺少复杂的人类写作风格中的“波动”与“细节”。人类写作往往会根据上下文、情感和个人经验进行调整，而AI则是根据概率生成句子，这可能导致某些不自然的语言现象。AI检测器可以通过对比这些特征来识别文本。
>
> 3. **缺乏深度理解**
>
> 虽然AI可以根据已有数据生成内容，但它并不具备真正的理解能力。AI生成的文本往往会给出合适的表面答案，但在深入分析、提供具体实例或者进行创造性思考时，往往显得空洞或模糊。AI检测器可以通过分析内容的深度与广度，判断文本是否具备足够的思考和逻辑推理。
>
> 4. **上下文不一致性**
>
> AI生成的内容在较长文本中可能会出现上下文的不一致。例如，AI有时会出现前后信息矛盾或者内容跳跃的情况，这在长篇的人工写作中是不常见的。AI检测器能够识别出这些不一致，从而判断文本是否由AI生成。
>
> 5. **词频与词汇使用**
>
> AI生成的文本中，某些词汇的使用频率较高，而且词汇可能会显得比较普通和通用。比如，AI在处理某些常见问题时，可能会倾向于使用一些标准化的词汇和表达方式，而缺少个性化的用词。AI检测器通过分析文本中的词频和词汇选择，能够判断文本是否人工生成。
>
> 6. **特征分析**
>
> AI检测器通常会利用机器学习技术，对文本进行特征提取，分析文本的句法结构、词汇模式、段落结构等，建立一个“正常人类写作”的模型。如果文本的特征与模型中的正常写作特征差异较大，就有可能是AI生成的。

##### Quillbot

（下文仍然会详细提到Quillbot，这里仅讨论Humanize功能）

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209011105170.png" alt="image-20250209011105170" style="zoom:33%;" />

Quillbot本身属于Paraphraser（转述和改写工具），先前的Quillbot本身不具备Humanize功能，需要使用Custom进行定制，效果非常一般。经过版本迭代，Quillbot终于不负众望推出了系统级的Humanize功能，效果远远好于先前使用Custom进行定制。

**未人格化：** <img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209015138377.png" alt="image-20250209015138377" style="zoom: 33%;" />

**人格化后：**<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209015251799.png" alt="image-20250209015251799" style="zoom: 30%;" />

##### WriteHuman

订阅费用：淘宝购买会员25-35/月

这是我近期才发现的一个宝藏的AI Humanizer，相比Quillbot，WriteHuman可以在保持低AI率的前提下，保证文章的学术性。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209121347124.png" alt="image-20250209121347124" style="zoom:33%;" />

上文相同文本使用Write Human进行人格化之后的AI率：

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209121534551.png" alt="image-20250209121534551" style="zoom: 33%;" />

##### Bypass AI

订阅费用：淘宝共享账号120/月

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209122400442.png" alt="image-20250209122400442" style="zoom:33%;" />

效果最好，但太贵，性价比太低，不推荐。

#### Paraphraser（转述工具）

##### Quillbot

订阅费用：淘宝独享账号100-120/年

![image-20250209123001555](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209123001555.png)

没有任何留子会对Quillbot不熟悉，不过Paraphrase是他最基本的功能，其拓展功能十分强悍

Grammar Checker：虽然名字叫“Grammar Checker”，现实中更多不只是用它检查语法错误，而是让Quillbot推荐文章哪里有问题，哪里可以更流畅

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209123154960.png" alt="image-20250209123154960" style="zoom:33%;" />

AI Detector：只要有会员可以无限制查AI率，相比起GPTZero免费版的限额和高昂的订阅成本，尽管Quillbot的检测略逊于GPTZero，但日常写作够用。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209134938700.png" alt="image-20250209134938700" style="zoom:33%;" />

Plagiarism Checker： 查重，Premium每个月限额600000字符

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209142200272.png" alt="image-20250209142200272" style="zoom:33%;" />

Summarizer：总结归纳用，感觉意义不大，不如用GPT总结，更加灵活

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209142301943.png" alt="image-20250209142301943" style="zoom:33%;" />

Translator：不推荐，不如DeepL好用

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209142432086.png" alt="image-20250209142432086" style="zoom:33%;" />

Citation Generator：这个不错，功能相较于其他的要丰富一些，下文会推荐更好用的Citation Generator。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20250209142443870.png" alt="image-20250209142443870" style="zoom:33%;" />

Quillbot Chrome Extension：不是很推荐，经常乱蹦出来，有点影响使用体验。

#### Grammarly

