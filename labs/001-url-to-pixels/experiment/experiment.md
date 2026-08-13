\# Experiment 001-A — Observe a Web Navigation



\## Objective



In this experiment, we will observe what happens when Chromium loads a web page.



The goal is not to prove every internal implementation detail.



The goal is to collect observable evidence and connect that evidence to the

architecture introduced in Lab 001.



\---



\## What We Are Investigating



We will investigate this portion of the journey:



User

&#x20; ↓

Omnibox

&#x20; ↓

Browser / Navigation

&#x20; ↓

Network Activity

&#x20; ↓

Web Server

&#x20; ↓

Response

&#x20; ↓

Renderer / Web Content



We will use Chrome DevTools to observe the network side of this journey.



\---



\## Difficulty



L2 — Observer



\---



\## Estimated Time



20–30 minutes



\---



\## Prerequisites



You should have:



\- Chromium installed.

\- Basic familiarity with URLs.

\- Basic understanding of HTTP/HTTPS.

\- Completed the Lab 001 README.

\- The Lab 001 architecture diagram available for reference.



\---



\# Part 1 — Start Chromium



Launch the Chromium browser.



For this first experiment, use a normal Chromium browser session.



If you are using a locally built Chromium executable, launch that build.



\---



\# Part 2 — Open Developer Tools



Open Chrome DevTools.



On Windows/Linux, you can use:



&#x20;   F12



or:



&#x20;   Ctrl + Shift + I



You should see the Developer Tools interface.



\---



\# Part 3 — Open the Network Panel



Select:



&#x20;   Network



The Network panel is our first observation instrument.



Before navigating to a page, make sure network recording is active.



\---



\# Part 4 — Clear Previous Activity



Clear the existing network entries.



We want the next navigation to produce a clean observation.



The objective is to make the experiment repeatable.



\---



\# Part 5 — Navigate to the Test Page



In the browser's address bar, enter:



&#x20;   https://example.com



Press Enter.



Observe the Network panel while the page loads.



Do not immediately inspect individual requests.



First, simply observe the complete activity.



\---



\# Observation 1 — How Many Requests?



Look at the Network panel.



Record approximately how many requests were generated.



Write down your observation:



&#x20;   Number of requests observed:



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



Do not worry if your number differs from another learner's result.



The exact request set can vary because browser state, caching, connection reuse,

extensions, platform configuration and other factors can influence a page load.



\---



\# Observation 2 — Identify the Main Document



Find the request corresponding to:



&#x20;   example.com



or the main document associated with the navigation.



Select that request.



Look at the information provided by DevTools.



Record:



&#x20;   Request URL:

&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   Request method:

&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   Status:

&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   Content type:

&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



\---



\# Observation 3 — Inspect the Response



Open the response information for the main document.



Look at the returned HTML.



Ask yourself:



> Where did this HTML come from?



The immediate answer is:



> It was returned by the web server as part of the HTTP response.



But this experiment is asking a deeper question:



> Which Chromium component obtained this response, and which component

> subsequently processes the web content?



Do not answer from memory.



Use the architecture diagram.



\---



\# Observation 4 — Inspect the Timing Information



Open the timing information for the main document request.



Look at the phases reported by DevTools.



You may see stages associated with activities such as:



\- Queueing

\- Connection

\- Request

\- Waiting

\- Download



The exact information displayed depends on the request and current browser state.



Record anything interesting:



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



\---



\# Observation 5 — Inspect the Initiator



If available for the selected request, inspect the Initiator information.



Ask:



> What caused this request to occur?



For the main document navigation, think about the relationship between:



&#x20;   User action

&#x20;       ↓

&#x20;   Navigation

&#x20;       ↓

&#x20;   Resource request



This is an important distinction.



The Network panel shows observable network activity.



It does not expose the complete internal Chromium call graph.



\---



\# Part 6 — Return to the Architecture Diagram



Now look at the Lab 001 architecture diagram again.



Locate:



&#x20;   Browser Process



&#x20;   Network Service



&#x20;   External World



&#x20;   Renderer Process



Compare those boxes with what you just observed.



\---



\# Correlation Exercise



Complete the following table.



| Observation | Architecture Component |

|---|---|

| User enters URL | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

| Navigation begins | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

| Network request occurs | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

| Web server responds | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

| HTML becomes available to the browser | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

| Web content is processed | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |



Do not expect DevTools to directly label every internal process.



The purpose of this exercise is to learn the difference between:



&#x20;   Observable browser behaviour



and:



&#x20;   Internal browser architecture



\---



\# Important Lesson



The Network panel is an observation tool.



It does not provide a literal window into every Chromium process.



For example, seeing an HTTP request in DevTools does not mean that the

Network panel is showing the internal implementation of Chromium's

Network Service.



Instead, we are using observable evidence to build and test an architectural

mental model.



This distinction becomes increasingly important in the later laboratories.



\---



\# Challenge 1



Reload the page.



Compare the second load with the first load.



Ask:



> Did everything happen exactly the same way?



Record your observations.



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



\---



\# Challenge 2



Open another simple web page.



Repeat the experiment.



Compare:



\- Number of requests

\- Resource types

\- Response status

\- Timing

\- Additional resources



Record at least two differences.



&#x20;   Difference 1:



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   Difference 2:



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



\---



\# Challenge 3 — Think Like a Chromium Engineer



Consider this statement:



> "I entered a URL and Chromium downloaded the page."



This statement is technically true but incomplete.



Try to improve it.



Write a more precise explanation using at least these terms:



\- Browser Process

\- Navigation

\- Network Service

\- Renderer Process

\- Web content



Your explanation:



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



&#x20;   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_



\---



\# Expected Learning Outcome



After completing this experiment, you should understand that a web navigation

is not simply:



&#x20;   URL → Web Server → Screen



Instead, Chromium coordinates multiple pieces of browser functionality.



At this stage, you should be able to explain the conceptual relationship:



&#x20;   User

&#x20;     ↓

&#x20;   Navigation

&#x20;     ↓

&#x20;   Browser-level coordination

&#x20;     ↓

&#x20;   Network activity

&#x20;     ↓

&#x20;   Response

&#x20;     ↓

&#x20;   Web-content processing



The later experiments will investigate what happens after the response

reaches the web-content side of Chromium.



\---



\# Evidence to Capture



For your laboratory notebook, capture:



1\. The Network panel showing the page-load requests.

2\. The main document request.

3\. The response information.

4\. The timing information.

5\. Your completed correlation table.

6\. Your answer to Challenge 3.



Screenshots should be used as experimental evidence rather than decoration.



\---



\# Questions to Think About



Before moving to the next experiment, try to answer:



1\. Where does navigation begin?



2\. Where does network activity become observable?



3\. Where does the web server fit into the architecture?



4\. Is the Network panel showing Chromium's internal process boundaries?



5\. What evidence do we have that the response reached the web-content side?



6\. What information is still invisible to us?



Question 6 is especially important.



It leads directly to the next stage of this laboratory.



\---



\# Next Experiment



\## Experiment 001-B — From Response to Rendered Web Content



In the next experiment, we will move beyond the Network panel.



We will investigate:



&#x20;   HTML

&#x20;     ↓

&#x20;   DOM

&#x20;     ↓

&#x20;   CSS

&#x20;     ↓

&#x20;   Layout

&#x20;     ↓

&#x20;   Paint

&#x20;     ↓

&#x20;   Compositing



We will use browser inspection tools to connect the visible page with the

rendering architecture introduced in Lab 001.

