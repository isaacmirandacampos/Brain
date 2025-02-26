# How use technology to apply Data Driven Design
created:: 2024-10-19 09:47
status:: #zettel/permanent 
tags:: #telemetry #tech-talk #product #data-driven-design

## What is Data Driven Design?
Data Driven Design is a practice of use data to make decisions rather than use the personal intuition. It's better for make new decisions and to validate decisions. It helps the team work on what's important. The data driven design has two segments of data, such as: quantitative data and qualitative date, we talk about quantitative data in this document.
## Why is important for TI?
Nothing goes write the best code with the best practices, if the best code not the best software for the user. Know the tools and use there for change our code is a essential practice for our. We can use some tools in our CI/CD for ensure the consistency practice.
## Data segments
The data of a digital product 
- Screen records
	- Understand user problems report.
	- See the user behavior, an example, if users are reading the message errors and modals.
- Heatmaps
	- Know the users focus the most considering your clicks, Scrolls and navigation.
	- Measuring the effectiveness of key content
- Experiment management
	- Compare strategies to known the most effectiveness
- Web page analytics
	- Know the accessibility level, performance, region available and seo.
- Business analytics
	- Understand the business health.
- Applications Monitor
	- Create metrics, example: response time, feature user rate/count, user satisfaction score, uptime percentage.
	- Create alerts, example: when has many users in the same minute trying use the application.
### Tools without code changes
Exist many tools to help us how know the quality the our softwares without code changes.
#### [PageSpeed Insights](https://pagespeed.web.dev/)
A tool that help the team know the performance of frontend.
- Compare desktop and mobile
- User metrics experiences (FCP, LCP and CLS)
- Accessibility
- SEO
- Best practices
#### [WebPageTest - Website Performance and Optimization Test](https://www.webpagetest.org/)
Help to known the performance of frontend too, but has other data.
- Geographical testing
- Mobile and desktop test
- Allow export the data
- Detailed possible optimizations.
#### [SpeedCurve | Website Performance Monitoring](https://www.speedcurve.com)
It's paid but allow you compare with other digital products.
### Tools self hosted with code changes
We can use google analytics for some data, but we can use other tools to measure the quality of front-end.
#### [Matomo | The privacy-friendly Google Analytics alternative](https://matomo.org/)
Open source tool made in php and mysql that allow know many interactions use.
demo: [Matomo](https://demo.matomo.cloud/index.php?module=CoreHome&action=index&idSite=1&period=day&date=yesterday#?period=day&date=yesterday&category=Dashboard_Dashboard&subcategory=1)
- heatmap
- session recording
- behavior
- visitors
#### [Ackee](https://demo.ackee.electerious.com/#/)
An open source tool made in node.js that how know the user interaction with our applications, the duration of sessions and the how use find the website.
demo: [Ackee](https://demo.ackee.electerious.com/#/)
## When don't known where go, any route will do
You don't use the data for the data, you need use the data to know the actual state, and after this, know what do you need improve. When do you know what you need improve, you can define how measure the effectiveness using data.
For create goals, you need known the actual state of your product/business. Don't feels afraid if you don't known your target, maybe you need study your business to known what do you need do.
## Tips of what we can try measure today
Some ideas of what do we can try measure and what tools used for this.
### Onboading app Rentbrella
The rate of users read the onboarding, abandon the onbarding in the middle and the persons don't read the onboarding. Know the time of a user use to withdraw in GC after skip onboarding, abandon in middle step and when complete the onboarding. Help us to understand the effectiveness the onboarding and make the decision about change the actual onboarding to an apply a guided onboarding.
**Tools:** heatmap and Applications monitor.
**Goals example:** Improve the medium time of new users the machine (we can attack the onboarding unread, onboarding medium or simplify the uses.)
### SLA of operation team
We can create a dashboard on murdock to known the medium time of OS be resolved or allocated. It's can be filtered by type of OS, operation group, third party service and region. We can known if a group or operator has difficult for a specific OS and to research the reason.
**Tools:** business analytics 
**Goals example:** Know what groups can improve your time and know which regions need more operators and which OS types cost most for the Rentbrella. With this, you can hire more operators, improve the onboarding of a operator group, research a possible path to avoid most expensive os types.
### Queue frequency
In some times, we talk about the queue users waiting to use our machines, but what the frequency of queues for rain? It's common? We can measure the time of a new user try to use the machine in a rain.
**Tools:** Applications monitor and business analytics
**Goals example:** Justify the withdraw using BLE.
