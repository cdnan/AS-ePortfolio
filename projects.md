---
layout: page
title: Projects
permalink: /projects/
order: 2
---
<style>
.code-collapse {
  max-width: 580px;
  margin: 0.25rem auto 1.5rem;
  text-align: center;
}
.code-collapse summary {
  display: inline-block;
  font-size: 0.82rem;
  color: #656d76;
  cursor: pointer;
  padding: 0.2rem 0;
  transition: color 0.15s;
}
.code-collapse summary:hover {
  color: #24292f;
}
.code-collapse pre {
  text-align: left;
  background: #f6f8fa;
  border: 1px solid #e1e4e8;
  border-radius: 6px;
  padding: 0.9rem 1.1rem;
  margin-top: 0.5rem;
  overflow-x: auto;
  font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
  font-size: 0.78rem;
  line-height: 1.65;
  color: #24292f;
  white-space: pre;
}
</style>

### 1. Understanding Canadian Attitudes Toward Cryptocurrency

Everyone has heard of cryptocurrency, but what do Canadians actually think about it? My research explored this question through original survey data collected across Ontario, Québec, and Alberta, uncovering a striking paradox: while awareness of digital currencies is nearly universal, actual ownership remains low and skepticism runs deep. 

<div style="text-align: center;">
  <img width="560" alt="awareness" src="https://github.com/user-attachments/assets/353af6a8-1347-4249-845f-f845117f21e2" style="height: auto;" />
</div>
<details class="code-collapse">
<summary>Show R code</summary>
<pre>ggplot(awareness, aes(x = aware, y = Percentage, fill = Group)) +
  geom_bar(stat = "identity", position = position_dodge()) +
  geom_text(aes(label = Percentage),
            position = position_dodge(width = 0.9),
            vjust = -0.3, size = 3) +
  scale_fill_manual(values = c("grey", "#7393B3", "black")) +
  labs(y = "Percentage (%)", fill = "", x = "",
       title = "Have you heard of cryptocurrencies (e.g., Bitcoin or Ethereum?)") +
  theme_minimal() +
  theme(legend.position = "bottom") +
  guides(fill = guide_legend())</pre>
</details>
<div style="text-align: center;">
  <img width="560" alt="ownership" src="https://github.com/user-attachments/assets/219790bd-2b4e-4029-a96f-8479a197db20" style="height: auto;" />
</div>
<details class="code-collapse">
<summary>Show R code</summary>
<pre>ggplot(ownCrypto, aes(x = ownership, y = Percentage, fill = Group)) +
  geom_bar(stat = "identity", position = position_dodge()) +
  geom_text(aes(label = Percentage),
            position = position_dodge(width = 0.9),
            vjust = -0.3, size = 3) +
  scale_fill_manual(values = c("grey", "#7393B3", "black")) +
  labs(y = "Percentage (%)", fill = "", x = "",
       title = "Do you currently own any cryptocurrencies?") +
  theme_minimal() +
  theme(legend.position = "bottom") +
  guides(fill = guide_legend())</pre>
</details>


What makes this particularly interesting is the unexpected fault lines I discovered. Rather than simple left-right political divides, the real story is generational. Younger and older members of the same political parties hold dramatically different views on cryptocurrency. These generational rifts within party coalitions could reshape how Canada approaches fintech regulation in the years ahead.

<div style="text-align: center;">
  <img alt="attitude_age" src="https://github.com/user-attachments/assets/85d510e4-ff33-4719-97c7-1ee2521fa8f5" style="max-width: 560px; width: 100%; height: auto;" />
</div>
<details class="code-collapse">
<summary>Show R code</summary>
<pre>ggplot(attitudes_age,
       aes(x = attitudes, y = Percentage, fill = age_group)) +
  geom_bar(stat = "identity", position = position_dodge(width = 0.9)) +
  geom_errorbar(
    aes(ymin = pmax(Percentage - MoE, 0),
        ymax = pmin(Percentage + MoE, 100)),
    position = position_dodge(width = 0.9),
    width = 0.2,
    color = "black"
  ) +
  scale_fill_manual(values = c(
    "#E6EDF3","#C9D6E3","#A9BCD0",
    "#8CA2BD","#6E88A8","#4F6E92","#2F567C"
  )) +
  labs(
    y = "Percentage (%)",
    fill = "",
    x = "",
    title = "How would you describe your opinion about cryptocurrencies in general?",
    caption = "Source: Authors calculations \nn=43,382"
  ) +
  theme_minimal(base_family = "sans") +
  theme(
    plot.title = element_text(size = 14),
    legend.position = "bottom")</pre>
</details>

This research provides a baseline of Canadian cryptocurrency attitudes and reveals why digital currencies, despite their ubiquity in financial news, continue struggling to gain public legitimacy. As policymakers grapple with how to regulate this space, understanding these public opinion dynamics becomes crucial.

**Reflection:** This project combines empirical analysis with a topic of growing societal, economic and political relevance — one that spans academic research, financial services, technology policy and consumer behaviour. Working with original survey data across three provinces pushed me to make careful decisions about how to visualize distributional data across multiple demographic groups in a way that was both rigorous and accessible. Writing up the findings for this portfolio, rather than for an academic audience, also challenged me to communicate statistical patterns as a narrative that non-specialists could engage with. The policy implications of this work — that public skepticism creates real barriers for regulators and industry actors exploring cryptocurrency initiatives — reflect my broader goal of producing research with practical relevance beyond the university.

Goal 2 ✅
Goal 3 ✅
Goal 4 ✅


### 2. The Impact of Framing and Elite Cues on Public Attitudes: The Case of Central Bank Digital Currencies

How susceptible is public opinion to various arguments on CBDCs? To what extent do elite cues on CBDCs affect public trust in the Bank of Canada to issue one? We know political messaging shapes public opinion, especially on complex topics where most people lack expertise. Central bank digital currencies (CBDCs) seemed like the perfect test case: a technical policy area where citizens should be particularly susceptible to guidance from trusted elites.

But my experimental research revealed something surprising: it doesn't always work that way. I designed a survey experiment (with my colleagues at the Digital Society Lab) exposing participants to different elite statements about CBDCs, from generic arguments to specific political endorsements. The theory was straightforward: positive frames should boost trust in the Bank of Canada to issue a digital currency, whereas negative frames would decrease trust. Instead, I found that most messaging fell flat, and political endorsements only moved the needle among partisans.

This matters because central banks worldwide are navigating increasingly politicized environments. If elite cues can't effectively build public support for technical monetary innovations, even in a "most likely" scenario with low public knowledge, it suggests the mechanisms of elite influence are more fragile than we thought. The findings challenge assumptions about how central bank legitimacy is built and sustained in an era of growing skepticism toward institutions.

<div style="text-align: center;">
  <img alt="prime-plot" src="https://github.com/user-attachments/assets/ef5a898b-acd2-4bc8-86ef-13da18776d45" style="max-width: 560px; width: 100%; height: auto;"/>
</div>
<details class="code-collapse">
<summary>Show R code</summary>
<pre>ggplot(results, aes(x = estimate, y = term)) +
  geom_point(size = 3) +
  geom_errorbarh(aes(xmin = conf.low, xmax = conf.high), height = 0) +
  geom_vline(xintercept = 0, linetype = "dashed", color = "red") +
  labs(x = "Marginal Effect", y = "") +
  theme_minimal()</pre>
</details>


**Reflection:** This project pushes beyond descriptive analysis into experimental methodology, testing not just what people think, but whether their views can be moved. Designing a survey experiment with colleagues deepened my methodological expertise and gave me hands-on experience with causal inference techniques in a real policy context. The finding that most elite messaging fell flat, and that political endorsements only shifted opinion among partisans, forced me to think carefully about how to present null and unexpected results in a way that was still compelling and policy-relevant. This project also connects to my goal of translating research into practical insight, the findings have direct implications for central banks and policymakers trying to build public legitimacy for digital currency initiatives in an era of institutional skepticism.

Goal 1 ✅
Goal 3 ✅
Goal 4 ✅

### 3. CryptoCommons: Tracking Canada's Digital Currency Policy Debates

What do Canadian politicians have to say about cryptocurrency? Despite international conversations and debates about regulating digital currencies and blockchain technology, there's been no systematic way to track who's saying what in Parliament (unless you're willing to comb through Hansard Debates, that is).

I created [CryptoCommons.ca](https://cryptocommons.ca/), a public database that documents every statement Canadian politicians make about digital currencies in the House of Commons. By consolidating scattered legislative discourse into one searchable platform, CryptoCommons.ca empowers researchers, journalists and citizens to understand where politicians stand and how policy debates evolve. 

See my presentation about CryptoCommons.ca at the Future of Finance Summit: [CryptoCommons.ca Lightning Talk (PDF)](https://github.com/user-attachments/files/24912900/CryptoCommons_LightningTalk.pdf)

**Reflection:** This project represents a different kind of contribution than the first two — rather than analyzing data, I built a tool to make data accessible. Creating CryptoCommons.ca required me to think about information architecture, database design and user experience in ways that go well beyond typical academic research. It also pushed me to consider what researchers, journalists and citizens actually need when trying to track policy debates, a practical design challenge that connects directly to my goal of translating academic work into something communities can use. Presenting this project at the Future of Finance Summit as a lightning talk was an exercise in distilling a complex resource into a concise, persuasive pitch for a non-academic audience.

Goal 2 ✅
Goal 3 ✅
Goal 4 ✅
