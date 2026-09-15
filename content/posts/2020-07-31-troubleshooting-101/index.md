---
title: "Troubleshooting 101"
author: "Ricardo Ferreira"
categories:
  - "DevRel"
  - "Technology"
  - "Troubleshooting"
date: 2020-07-31
nolastmod: true
draft: false
---
Part of my job as Developer Advocate is to reach out to developers in social forums like Stackoverflow, Reddit, and Slack communities to check whether I can provide help. While I feel great pleasure in doing this, it is getting harder and harder to help people these days.

![](https://tr3.cbsistatic.com/hub/i/2017/03/23/8a2e6afc-25d6-4993-b60a-0c36a1502e4d/4r2wao.jpg)

I have the feeling that developers these days don't know (or perhaps forgot or pretend that they forgot) how to perform basic troubleshooting. Every time I see a request for help in a forum usually people barely explain what the problem is, how it occurs, give evidence of what happened before the incident and, more importantly, to provide a minimal explanation of their environment.

As a consequence, it is common to see questions like this:

![](image-1024x672.png)

Believe or not; this is the end of the question asked on Stackoverflow. Now, before getting into the real troubleshooting 101 section, I would like to highlight what is wrong with this request:

1\. "in the second" what? Second cluster? Second topic? You meant "in this moment"?

2\. Got it, you're using Strimzi. What version/release?

3\. "In some connectors" could you please be less obscure and share which connectors?

This request is a good example of question that, though I would like to help, I simply can't. There is not enough information provided in the question and in order to help I would need to spend some considerable time posting comments to explore the missing items to then, be able to help. My takeaway from this is that is not worth try to help. Shame on me? I don't think so. I can't waste cycles of my work in something that would consume several hours or maybe days if the person is on a different timezone.

Now, I totally sympathize with situations like this. I have been there before. From time to time I am there as well since I am still a developer. But if there is one thing that every developer must learn on their early days is how to perform good troubleshooting. Even when the intention is to ask for help. This is particularly true if you are going to ask for help in a forum where people will help you in their free time/will.

But this skill should be practiced as well even if you are going to ask for help in a paid customer support channel. Back in my days with Oracle I used to help the support team with critical escalations related to Java, Fusion Middleware, and SOA technologies. It was amazing (actually it wasn't, I am being sarcastic now) how incomplete and confuse the requests were. So even if you are a customer of a given product, please take the effort to help a sister/brother out.

### **Five Simple Steps**

I like to explain that troubleshooting has more to do with effort than complexity. It is not complex and anyone can do it. But it requires, effort, discipline, and consistency. Here is five steps to get you there.

\- **Own the problem** : Nobody on earth will ever possess a clear picture of the problem than you. Make sure to provide enough details and not just flush your frustration in a form of a _help me_ request. By giving enough details you can share with everybody else not only what the real problem is but also -- what the problem means to you. This is important because sometimes people won't be able to fix the problem right away but if they have a clear picture of what you are expecting with the fix, they can provide alternate solutions.

\- **Describe the environment** : Software have a natural course of being created, generate bugs, get those bugs fixed, and then release and repeat. What this means is that you need to be extra careful in providing enough information about the problem. A problem might occur in v1.3 but not anymore on v1.5. Describe details such as which operating system was being used, versions, custom configuration applied, grab different traces of the error in different time frames (sometimes the error change with time), share if it happens in other environments and/or with different configurations.

\- **Share the steps** : "Hey, I tried to calculate 2 + 2 and the result wasn't 4." OK great, but how did you tested this? You need to provide the exact steps you took to test something because sometimes might be a simple problem of trying to test something wrongly. We all know that 2 + 2 = 4 but perhaps you might be trying to do this so uniquely to your use case that -- depending of the steps you took -- you ended up with a different result. And in the case of trying 2 + 2 and getting a number different than 4, it becomes even more important to share what exactly did you do don't you think?

\- **Simplify the effort** : This has to do with what was said above regarding sharing the steps but it is important to describe what you have done until you decided to ask for help. This is important because it provides empathy. You can't simply ask for a person to own your problem. If you don't share what you have done before the person trying to help you will need to start their investigations and troubleshooting exercise from the beginning. If you share what you have done; they can reuse that effort. Oh, and here is a tip: if you don't share what you have done people might ask you this anyway just to measure how hard have you tried. If you are unable to share what you have done, they will leave you on the spot because you are not trying hard. Nor should they, right?

\- **RTFM** : I can't exhaust enough the idea of reading the documentation before raising a issue. I am not going to defend documentation because I know that some of them really suck; but in most cases they help you to fix problems. Sometimes is not that the answer to your specific problem will be there -- which indicates that you started doing something without reading the docs and then decided to read reactively. What I am saying is that if you, before start building something, read the docs to make sure that you follow the exact steps that the provider wants you to follow, will be able to minimize a lot your chances of doing something wrong in the first place. And if it happens, people will at least know that this might be either a bug or something that the software haven't predicted. Always file a JIRA if that happens, BTW.

### **Conclusion**

If the feeling that you have right now after reading this post is that there is a lot of work to even ask a question, then you got the point of it. Asking technical questions in forums or support channels shouldn't be a matter of "hey here is my problem, solve it bitch" but instead, should be you asking for a collaborative effort in solving the problem that no one else owns but you. Therefore, any help provided should be honestly greatly appreciated.

And you don't greatly appreciate something just because you wrote in the end of your request the sentence "Any help will be greatly appreciated". Appreciation will happen if whoever decides to help you see that you are not just throwing your problems over the wall but are looking for collaboration and partnership.
