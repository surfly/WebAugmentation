---
title: Webfuse Technical Whitepaper
date: 2025-03-28
draft: false
slug: webfuse-technical-whitepaper
---
# Webfuse Technical Whitepaper

##

[Introduction	4](#introduction4)
[Background & Challenges	5](#backgroundchallenges5)
[Existing Solutions & Their Limitations	5](#existingsolutionstheirlimitations5)
[The Need for Webfuse	5](#theneedforwebfuse5)
[What is Webfuse?	6](#whatiswebfuse6)
[Webfuse Virtualization Layer	6](#webfusevirtualizationlayer6)
[Webfuse Concepts	7](#webfuseconcepts7)
[The Virtual Web Session	11](#thevirtualwebsession11)
[Domain and Application Rewrite	11](#domainandapplicationrewrite11)
[Running In A Virtual Tab	11](#runninginavirtualtab11)
[Advanced Interaction and Analytics	12](#advancedinteractionandanalytics12)
[Fully Customizable	12](#fullycustomizable12)
[Webfuse Functionality	13](#webfusefunctionality13)
[Customize	13](#customize13)
	[Custom Domain Mapping	13](#customdomainmapping13)
	[Randomized Domain Mapping	14](#randomizeddomainmapping14)
	[Custom Landingpage	15](#customlandingpage15)
	[Region Pinning  ADD-ON	15](#regionpinningaddon15)
	[Residential IP ADD-ON	15](#residentialipaddon15)
[Extend	16](#extend16)
	[Session Events and Actions	16](#sessioneventsandactions16)
	[Virtual Web Extensions	17](#virtualwebextensions17)
[Secure	21](#secure21)
	[Participant Authentication and or Verification	21](#participantauthenticationandorverification21)
	[Cookie Guard	22](#cookieguard22)
	[Additional Request and or Response Headers	23](#additionalrequestandorresponseheaders23)
	[Lockdown APP ADD-ON	23](#lockdownappaddon23)
[Observe	25](#observe25)
	[Web Session Audit Logs	25](#websessionauditlogs25)
	[Session Recording	26](#sessionrecording26)
	[Content Masking	27](#contentmasking27)
[Collaborate	28](#collaborate28)
	[Session Sharing	28](#sessionsharing28)
	[Video Calling	31](#videocalling31)
[Automate	32](#automate32)
	[Automation API	32](#automationapi32)
	[Virtual Participant Functionality	34](#virtualparticipantfunctionality34)
[Technical Architecture	35](#technicalarchitecture35)
[System Architecture	35](#systemarchitecture35)
[Content Rewriting and Modification	37](#contentrewritingandmodification37)
[Security & Privacy	39](#securityprivacy39)
	[Key Security & Privacy Features	39](#keysecurityprivacyfeatures39)
[Integrating Webfuse	40](#integratingwebfuse40)
[Session Creation	40](#sessioncreation40)
[Magic Link Functionality	41](#magiclinkfunctionality41)
[Embedding Webfuse Sessions - Widget API	41](#embeddingwebfusesessionswidgetapi41)
[Extending Functionality - Extensions API	43](#extendingfunctionalityextensionsapi43)
[Automating Sessions - Automation API	44](#automatingsessionsautomationapi44)
[Deploying Spaces and Extensions	44](#deployingspacesandextensions44)
## 
# Introduction

Remix the Web

The web was born as an open, interconnected space?a place where information flowed freely, innovation thrived, and anyone could build upon what came before. But over time, that vision has faded. Today, web applications exist within walled gardens, tightly controlled ecosystems that make modification difficult, integration complex, and innovation sluggish. Developers are burdened by rigid third-party dependencies, compliance constraints, and lengthy development cycles just to implement basic changes.

Yet, some of the greatest technological leaps haven?t come from tearing everything down and starting over?they?ve come from remixing, reimagining, and extending what already exists. Google?s early motto, *"Standing on the shoulders of giants,"* captured this idea: true innovation comes from building upon the foundation laid by others.

Think about the tape recorder. At first, it was just a way to copy music, but in the hands of creative minds, it became a tool of transformation. It birthed the mixtape culture, where people curated and remixed their favorite sounds, breaking free from the control of record labels. It gave rise to hip-hop, where DJs looped beats and scratched vinyl, creating entirely new forms of expression. It reshaped how music was shared, consumed, and created.

Webfuse is doing the same for web development. Instead of being locked into rigid, vendor-controlled applications, developers can now remix the web itself. Web Augmentation is the mixtape revolution for the internet?allowing developers to modify, automate, and extend web applications instantly, without waiting for vendor approvals, backend access, or costly infrastructure overhauls.

With Webfuse, developers can take control of any web experience. They can bridge incompatible tools, enhance user interfaces in real time, and automate workflows that were previously locked behind proprietary barriers. The web doesn?t have to be static, slow, or unchangeable?it can be dynamic, adaptable, and responsive to your needs.

This whitepaper will show you how Webfuse makes this possible, breaking down the technology, the use cases, and the limitless possibilities of Web Augmentation. The next era of web development isn?t about tearing down and rebuilding?it?s about taking the fragmented pieces of the web and remixing them into something better.

# Background & Challenges

The complexity of the modern web, with its legacy applications, third-party integrations, and rigid development cycles, makes change costly and time-consuming, hindering developers instead of empowering them.

## Existing Solutions & Their Limitations

| Remote Virtual Browsers | Browser Extensions | Edge Workers & WAFs |
|---|---|---|
| Cloud-based browsers stream rendered content to users, avoiding direct modifications to web applications. While this prevents compatibility issues, it comes at a cost?high latency, degraded performance, and an experience that feels disconnected from the real web. | Extensions can modify web experiences in real-time, but they require users to install software, making large-scale deployment difficult and it is very difficult to make this operate as a single service.
 | Web Application Firewalls (WAFs) and Edge Workers allow developers to inject changes at the network level, but they require full control over routing and infrastructure?something you can only apply to those assets you CAN control and OWN. Not something you can apply to 3rd party or external resources.  |

## The Need for Webfuse

Instead of forcing developers to choose between slow, restrictive workflows or invasive infrastructure changes, Webfuse introduces a third path: **Web Augmentation.**

By leveraging **Virtual Web Sessions**, Webfuse makes it possible to modify, automate, and extend *ANY* web application instantly?without touching their source code, installing software, or waiting for vendor approval. Whether you need to enhance legacy applications, deploy real-time UI changes, or automate workflows across different platforms, Webfuse gives you full control over the web?without the usual friction.

# 

# What is Webfuse?

Webfuse is a **Web Augmentation Platform** that gives developers the power to remix, extend, and redefine any web application?without waiting for vendor updates, backend access, or infrastructure changes. Built on **Virtual Web Sessions**, Webfuse makes it possible to modify functionality, integrate automation, and create entirely new products on top of existing web apps.

- **Customize & Extend** ? Inject new UI elements, modify workflows, and build innovative experiences on top of any web application.

- **Secure & Observe** ? Enforce authentication, access control, and compliance with session-based security, audit logs, and all encompassing session recording.

- **Collaborate & Automate** ? Integrate AI-driven automation, orchestrate workflows across web apps, and enable seamless multi-user collaboration.

## Webfuse Virtualization Layer

A Webfuse **Virtual Web Session** is created when a user accesses an augmented application. Webfuse acts as a proxy-based environment where:

- Web content is dynamically rewritten.

- JavaScript execution is sandboxed for security.

- Requests are routed securely through Webfuse servers.

Webfuse provides a **REST API** and **JavaScript API** to control session behavior programmatically:

- **Session API** ? Start, modify, and control sessions.

- **Magic Links API** ? Generate JWT-secured session links.

- **Extension API** ? Deploy custom JavaScript enhancements.

# 

# Webfuse Concepts

Webfuse introduces a new way to interact with and modify the web, built on key concepts that enable full control, security, and extensibility.

**SPACE \
**A SPACE is a unique, customizable environment within Webfuse that acts as a container for SPACE SESSIONS. A SPACE is accessed via a SPACE LINK, which can include an optional LANDING PAGE and authentication settings.

**SPACE SLUG \
**A SPACE SLUG is the human-readable short name for a space, used in shareable URLs and embed links. It appears in public-facing links like: [https://company.webfuse.com/+](https://company.webfuse.com/+)<slug>/

**SPACE ID \
**A SPACE ID is the unique internal identifier of a Webfuse Space. It is used in API calls, SDK integrations (like the Widget API), and backend systems to reference and interact with a specific space. When opening a SPACE in studio you can see the SPACEID in the URL as follows: [https://webfuse.com/studio/spaces/{space_id}/](https://webfuse.com/studio/spaces/{space_id}/)

**CUSTOM DOMAIN** \
A CUSTOM DOMAIN allows you to serve your SPACE using a domain you own (e.g. `session.acme.com/+demo/`) instead of the default Webfuse subdomain (e.g. `acme.webfuse.com/+demo/`). This enables first-party cookie support, bypasses iframe restrictions, and allows you to white-label the experience for your users.

**LANDINGPAGE \
**A LANDINGPAGE is an optional page which can be displayed when opening a SPACE LINK. This page can show information regarding the space, collect user information or show terms of services and can be easily customized. 

**SPACE SESSION \
**A SPACE SESSION starts after a participant has opened a SPACE LINK, accepted the possible optional terms of service and has passed all identification requirements. Each session has its own START TIME, and will continue to exist until it is ENDED which results in a certain DURATION.

**SESSION EDITOR \
**A SPACE ADMIN can open the SESSION EDITOR where it can be used to install APPS, EXTENSIONS  or can be used to change the session settings. 

**START PAGE** \
One of those settings that can be changed, is the configuration of the  START PAGE. This is the specific URL to be opened at the start of a session, it is also possible to set this to pre-defined HTML content to enable more freedom and customization.

![](/images/rAZ_Image_1.png)

**VIRTUAL TAB** \
A VIRTUAL TAB is a sandboxed browser context running inside a Webfuse SESSION. Each tab represents an isolated web page, loaded through Webfuse?s proxy infrastructure, and rendered within the SESSION interface. Multiple tabs can exist simultaneously, and each tab has a TAB OWNER who controls its content.

**SESSION EXTENSIONS**** \
**A SESSION EXTENSION refers to a custom Javascript code module that can be loaded into a Webfuse SPACE SESSION to extend functionality and customize the user experience. These modules follow the regular Browser Extension API loosely and can be provided by anyone. 

**SESSION APPS \
**Session APPS are additional modules of functionalities which can be added to a SPACE to change its functionality. They are provided and managed by the Webfuse Team. Think of functionality such as Element Masking, Recording, Video Calling, Residential IP's, Storage Endpoints. 

**SPACE TYPE \
**We identify 4 different space types which will define how the space will behave:

- **SOLO** \
Only one participant is allowed to enter a session. Each user that opens a SPACE LINK will be put into their own SPACE SESSION.

- **SHARED \
**A shared session can be shared with multiple participants. We will enable the visual options within the UI to invite external users and the TAB BAR will show who actually owns a certain tab. 

- **MEETING \
**A meeting space is in essence a SHARED SPACE, but the original SPACE LINK will be converted into the SPACE SESSION LINK. This makes it possible to plan sessions ahead of time. 

- **ASSIST \
**Similar to a SHARED space, but sessions will be QUEUED and can be answered to enable a support like flow. 

 **PARTICIPANT PANEL \
**The PARTICIPANT PANEL lists all session participants and provides options to invite or remove participants. This is available for a SHARED, MEETING or ASSIST spaces. 

**SESSION ROLES** \
Within a SPACE SESSION we identify the following roles for participants:

- PARTICIPANT - any user who partakes in a session is a participant.

- SPACE ADMIN - any participant who has special ADMIN rights as defined on the SPACE membership list.

- TAB OWNER - any participant who opens content within a VIRTUAL TAB will be the TAB OWNER for that specific TAB.

- HOST - a special role which applies to a SHARED SPACE, in such a session a HOST will always need to be present in order for the session to be able to start.

**COLLABORATION MODE \
**We offer two different collaboration modes how SHARED SPACE can operate:

- In the PRESENTER MODE there will be one HOST and he defines what other participants of the session will be able to actively see. If during this mode, the HOST leaves, the session will end

- In the HUDDLE MODE there is no single host but each participant can freely change their view, they can see any of their own tabs or follow any of the other participants.

**COMMUNICATION PANEL** \
An integrated chat and video conferencing tool that enables real-time communication between participants.

**SESSION LIFETIME \
**A key feature of a SPACE session is that it has an explicit lifetime. The session starts as soon as the session is created and ends either when the session is explicitly ended or when there are no longer any active participants in the session. 

**ACTIVE PARTICIPANT** \
An active participant is a participant that has a working network connection with Webfuse - if the user has no active connection for more than 30 seconds (this is configurable) - we will terminate the session. This is intended behavior to actually reduce extraneous costs to be incurred on your behalf. 

**SESSION ACCESS CONTROL** \
When opening a SPACE LINK, we will go through a few steps before jumping into the session.  This is depicted below. 

![](/images/w9N_Image_2.png)

After opening a SPACE LINK, we check if we need to display a LANDINGPAGE, Is access restricted to certain members? Do  users need to identify themselves? Can the user obtain HOST rights or does he need to be ADMITTED and will the user end up in its own SPACE SESSION or a shared MEETING SPACE MEETING LINK.

**MAGIC LINK** \
It allows you to define session behavior (participant name, email, tabs, roles, permissions) and bypass SPACE authentication. Magic Links are encoded as a JSON Web Token (JWT) and signed using the SPACE REST KEY and can be generated on demand without contacting the Webfuse server.

**SPACE REST KEY** \
A secret token used to interact with a specific SPACE via the REST API. It allows session-level actions such as signing MAGIC LINKS, controlling session behavior, and accessing webhooks. This key is scoped to a single SPACE. This KEY should not be shared publicly!

**WIDGET KEY \
**A unique public identifier assigned to each SPACE. It is used when initializing a Webfuse SPACE via the JavaScript Widget API. The widget key determines which SPACE should be loaded, and is required to embed Webfuse inside your own application or webpage.

# The Virtual Web Session

A Virtual Web Session provides a controlled and dynamic environment for interacting with web applications without modifying their source code. Unlike traditional browser-based interactions, where users engage with web applications directly, Virtual Web Sessions introduce an intermediary layer that enables real-time augmentation, automation, and security enhancements. By operating at the presentation layer, Webfuse ensures seamless interaction with web content while maintaining high performance and security compliance.

## Domain and Application Rewrite

In a session, the original domain is replaced with a Webfuse-specific domain. For instance, if you would augment `salesforce.com``,` the virtual session will run under a domain such-as[ ](http://salesforce.webfuse.com)`salesforce.webfuse.com`.

All content retrieved during the virtual session is routed through Webfuse. This includes style sheets, JavaScript files, and other web resources such as images, fonts, and videos. The transformation occurs in real-time, with the platform dynamically rewriting the source code of the original application. This process happens within milliseconds, ensuring a seamless experience, and can leverage caching (where allowed) to improve performance.

Dynamic content, such as JavaScript code, is executed within the Webfuse sandbox, ensuring that it runs safely within the browser. Since everything is rendered and executed on the client-side, the quality remains intact, and there's no need to rely on a remote browser, eliminating any potential latency issues.

## Running In A Virtual Tab

Traditional browser sessions rely on client-side state management, using request headers, URL parameters, and authentication tokens (cookies, local storage, session storage) to persist user identity and session context. Webfuse extends this behavior by virtualizing the browsing experience within a **virtual tab**, enabling deep control over session behavior without requiring modifications to the original application.

A key architectural component of a Virtual Web Session is its stateless proxy mechanism, which transparently forwards requests between the user and the original web application. This ensures that the session maintains authentication and context while remaining fully isolated from the host environment. Unlike traditional browser extensions or middleware solutions that require direct integration, Webfuse operates independently, making it ideal for third-party augmentation, security testing, and automation workflows.

Beyond virtualization, Webfuse provides fine-grained control over the session lifecycle. Developers can interact with the virtual session via Webfuse APIs, enabling operations such as **programmatically opening or closing tabs, inviting participants into a shared session, or terminating a session when specific conditions are met.** Throughout its lifecycle, the Virtual Web Session logs various events, including session creation time, user join/leave events, navigation activity, and URL transitions. These events can be monitored using JavaScript event listeners or webhooks or recorded as an all encompassing video stream. 

## Advanced Interaction and Analytics

Traditional web analytics provide an incomplete picture of user behavior?tracking clicks, page loads, and referral sources, but failing to capture **what actually happens within a session**. Most solutions rely on embedded scripts, requiring modifications to the original application, which is often impractical for third-party platforms or legacy systems.

Webfuse **changes the game** by offering **deep session insight** without requiring any changes to the underlying application. Every Virtual Web Session automatically generates:

- **? Audit Logs (JSON-based event tracking)** \
Capturing granular user interactions, including:

- Form fields modified

- Clicks on specific UI elements

- Page transitions and navigations

- Other meaningful session-level events

- **?? Full Video Recording (MPEG)** \
A pixel-perfect replay of how the session was rendered for the original user, providing unmatched visibility into user behavior and engagement.

## Fully Customizable

A virtual session link can be opened directly in a browser or embedded within an existing web application using an IFRAME element. This flexibility allows you to create new experiences by integrating any external web application into your own environment. You can configure all visual aspects of the virtual session to align with your desired look and feel.

## 
# Webfuse Functionality

## Customize

### Custom Domain Mapping

Webfuse allows you to customize the domain under which the platform operates, providing the flexibility to run the original application under your own domain name. Typically, when augmenting an application running on "[http://example.com](http://example.com) ," the new domain would be something like "[example-com.webfuse.com](http://example-com.webfuse.com)." However, with custom domain mapping, you can modify this to reflect your own domain name, such as "[example-com.mydomain.com](http://example-com.mydomain.com)." This has two major benefits: The augmented application is now recognized as **first-party**, allowing it to bypass restrictions that typically apply to third-party domains, such as cookie access and security policies. Secondly Webfuse automatically makes the content **modifiable and embeddable**, overriding any restrictions that the original application may have placed on iframe embedding or UI modifications.

```
? Use-case: Embedding third-party content that cannot be embedded
Many modern web applications enforce strict Content Security Policies (CSP) or set a X-Frame-Options:Deny header, preventing their content from being embedded in iframes or displayed within external applications. This creates challenges for organizations that need to integrate third-party tools, dashboards, or applications into their own platforms.
For example, an enterprise CRM system wants to embed an external analytics dashboard from "https://analytics.example.com", but its own  CSP policy restricts third-party embeds, the X-Frame-Options header on the analytics embed  prevents iframing.
However, Webfuse creates a Virtual Web Session that dynamically rewrites the analytics dashboard?s domain and headers, allowing it to be embedded without the need to modify the original application or make an exception in the Content Security Policy.
How It Works with Webfuse:
Configure your Custom Domain (fe 'yourdomain.com') in Webfuse
Create a Webfuse SPACE
Set the START PAGE to https://analytics.example.com
Embed the Webfuse SPACE LINK
```
### Randomized Domain Mapping

Webfuse can also  generate unique domain names for each individual virtual web session. This enables you to create augmented versions of applications that appear as distinct and unrelated URLs, providing additional privacy and reducing potential security risks. For example, an augmented version of "[http://example.com](http://example.com) " might appear as "[d35ab8f1-f50f-41e6-b76d-7481e6c43783.webfuse.com](http://d35ab8f1-f50f-41e6-b76d-7481e6c43783.webfuse.com)" in one session and "[b11b9799-a0fc-4b67-8e46-e87fd418bc3e.webfuse.com](http://b11b9799-a0fc-4b67-8e46-e87fd418bc3e.webfuse.com)" in another.

This randomized domain mapping has significant implications:

- **Unique Sessions \
**Each virtual session is unique to the browser, enhancing privacy by preventing cookies set during one web session from being passed to another session. The drawback is that browser caching won't be utilized, potentially leading to reduced performance.

- **DNS Obfuscation \
**By encoding the target domain, this approach prevents "browsing leakage." through DNS lookups. Since DNS requests no longer expose target domains. 

```
? Use-Case: Preventing Tracking & Fingerprinting in Embedded Content

Web-based email clients often display external content, such as articles, product previews, or documents, within their interface. However, clicking on an external link exposes users to tracking mechanisms, allowing third-party sites to collect cookies, fingerprint devices, and link user activity back to their email identity.

With Webfuse?s Randomized Domain Mapping, email providers can open external content in a fully isolated session, ensuring: No tracking persistence ? Cookies, local storage, and session data are cleared per session. No fingerprinting ? Every session appears as a new, unrelated user to the destination site. Anonymous link tracking ? Websites cannot associate multiple visits to the same user.

How It Works with Webfuse:
Create a Webfuse SPACE
In the SPACE SESSION SETTINGS, enable RANDOMIZED DOMAIN MAPPING
Use the Magic Link API to create an embeddable SPACE SESSION LINK
Embed that SPACE SESSION LINK within your email provider instead of the original link.

The user who now opens the resulting SPACE SESSION LINK will everytime open each session in an empty context making them no longer trackable. Optionally we provide even more fine-grained control by using the 'Lockdown APP'. 
```
### 
### Custom Landingpage

The Webfuse Landing Page serves as the customizable entry point to your Virtual Web Session, designed to provide essential pre-session information, gather user consent, or enforce authentication and compliance requirements. One can leverage Webfuse Studio?s WYSIWYG editor to design a landing experience or Developers can upload fully customized HTML, CSS, and JavaScript to ensure a seamless transition into the session.

### Region Pinning  **ADD-ON**

Requests to the original server are routed through the Webfuse platform, with each user connected by default to the Webfuse server closest to their location. However, you can configure the platform to use a specific geographical region, effectively allowing you to simulate browsing the original website from different locations. This feature  gives you the flexibility to control the perceived origin of your web requests.

```
? Use-case: Bypassing Geo-Restrictions & Selective Censorship
Some governments and corporations restrict access to certain websites based on DNS filtering or blacklist policies. If a domain is flagged and blocked, users in certain regions are unable to access critical resources. 
Using Webfuse, however, one can connect to the nearest Webfuse server and then reroute the outbound request to originate from a specific server over an encrypted tunnel making it harder for firewalls and ISP's to block content. Using this solution, one can offer secure access to censored content without relying on traditional VPN's or Proxy Networks. With Webfuse, websites will remain fully functional while appearing under a different dynamic sub-domain every time. 
How It Works with Webfuse:
Create a Webfuse SPACE
In the SPACE SESSION SETTINGS:
Enable RANDOMIZED DOMAIN MAPPING
Install the Connections APP and configure your preferred region
Then either make the Space LINK available to users or Use the Magic Link API to create an embeddable SPACE SESSION LINK
```
### Residential IP **ADD-ON**

Webfuse aims to operate as transparently as possible, sitting between the host browser and the origin server to handle requests on behalf of the user. Despite this, two critical changes occur that might alter the perceived identity of the requestor: the IP address and the Transport Layer Security (TLS) fingerprint. Webfuse will adjust the TLS fingerprint to closely resemble that of the original requesting browser.  The IP address of the requestor, however,  changes to the Webfuse platform's IP. This shift in IP address may raise concerns if origin servers (or WAF?s) are specifically  monitoring for this. With this ADD-ON  the requests will be routed through  a residential network before hitting the origin server.

## Extend

### Session Events and Actions

Certain actions that happen within the session will trigger an event which can be tied to a certain WebHook defined by you. The **EVENTS** that we support are:Session Started, Session Ended, Page Relocation

But this can be extended further by yourself by leveraging our Virtual Web Extension API.

Next to that, each Virtual Web Session has its own API Endpoint to trigger certain **ACTIONS** such as: End the Session, Navigate to a Location, Load a Piece of Code, Send an API Message to Space Session

This functionality makes it possible to add full API functionality to any web interaction.

```
? Use-case: Enforcing Secure, Time-Limited Access to Premium Content
Imagine an online museum that offers paid access to high-resolution images. Traditionally, implementing a secure access-control system within an existing web-based image gallery would require extensive backend changes, complex authentication flows, and ongoing maintenance.
With Webfuse, the museum can instantly enforce access restrictions without modifying the original application. By routing user sessions through Webfuse, access control becomes seamless?users can be granted time-limited access without needing complex infrastructure changes.
How It Works with Webfuse:
Create a SPACE ? Define a controlled Webfuse environment.
Set the START PAGE ? Point it to the museum?s Image Gallery URL.
Enable ACCESS CONTROL ? Restrict access based on authentication rules.
Enforce Session Limits ? Use the REST API to define time-based access or embed a Virtual Web Session Extension to dynamically control session expiration.
The museum gains a secure, scalable solution for managing paid content access without altering its existing platform?ensuring compliance and reducing development overhead.
```
### Virtual Web Extensions

With Webfuse Virtual Web Extensions, you can rewrite the web in real time?adding new functionality, automating workflows, and customizing interfaces without waiting for vendor approvals or backend access.

Unlike traditional browser extensions that require installation and permissions, Virtual Web Extensions run inside a Webfuse session, allowing instant deployment across users, teams, and organizations.

Built on the familiar WebExtension API, Virtual Web Extensions let you:

- Add custom UI components to enhance the user experience.

- Run background scripts for deeper session control.

- Inject content scripts to modify the functionality and appearance of any web application.

This provides an incredible amount of flexibility where any browser extension can now be converted into an online service where it will be available to the world with just a single click.

```
? Use-case: Enhanced Marketing Attribution
Traditional URL shorteners only track the initial click, providing limited visibility into user behavior beyond the first interaction. Marketers struggle to measure true conversion impact, especially on third-party sites like e-commerce platforms where tracking is restricted.  Webfuse solves this by enabling full-funnel tracking on any website ? even sites you don?t control ? without requiring backend access or vendor cooperation.

How It Works with Webfuse:
Create a SPACE to generate a Webfuse-powered campaign link (instead of a standard URL shortener).
Open the SPACE SESSION and add a Custom Extension
Inject a tracking script (e.g., GTM, Segment, or a custom analytics script) using a Content Script
Share the resulting SPACE LINK in your campaign as the tracking-enabled URL.
The end result will be that instead of just knowing that 10,000 people clicked your campaign link, Webfuse lets you see that 1,200 people added products to their cart, and 400 completed purchases totaling $125,000 in revenue.
```
```
? Use-case: Enhance Web Accesibility & Compliance
Many organizations face legal and regulatory requirements  to ensure web applications are accessible to diverse audiences, including users who speak different languages or require usability enhancements due to disabilities. However, businesses often lack direct control over third-party platforms, making compliance difficult without vendor cooperation. 
Webfuse solves this by allowing organizations to dynamically translate web applications, improve usability, and ensure compliance?without requiring modifications to the original platform.
Relevant Compliance frameworks: 
Americans with Disabilities Act (ADA): On April 24, 2024, the Department of Justice published a final rule requiring state and local governments to ensure their web content and mobile apps are accessible, aligning with WCAG 2.1 Level AA standards.
European Accessibility Act (EAA): Effective June 28, 2025, the EAA mandates that products and services, including websites and mobile apps, comply with accessibility requirements across EU member states. ?
Health and Human Services (HHS) Rule: For recipients with 15 or more employees, compliance with WCAG 2.1 AA is required by May 11, 2026; 
How It Works with Webfuse:
Create a SPACE for the target Web Application
Open the SPACE SESSION and add a Custom Extension
Inject a Content Script to translate interfaces using API like Google Translate or DeepL, modify UI elements and or add assistive features. 
Share the SPACE LINK - or redirect the user automatically to the SPACE LINK
Webfuse enables organizations to dynamically enhance web applications, ensuring they meet accessibility standards without altering the original codebase.?
```

```
? Use-case: Deploy a Digital Adoption Platform (DAP) on Any Website
Traditional Digital Adoption Platforms (DAPs) like WalkMe, Pendo, and Userpilot are powerful, but their deployment is often limited to web applications you control. Rolling out a DAP across third-party SaaS tools, partner portals, or legacy applications typically requires vendor cooperation, backend integration, or browser extension installation?creating significant barriers.
Webfuse removes these limitations by enabling DAP deployment on any website?without requiring direct integration, browser extensions, or IT intervention. With Webfuse, you can overlay a DAP of your choice onto any web app instantly, ensuring guided workflows, tooltips, and automation work wherever you need them.
How It Works with Webfuse:
Create a SPACE ? for the target web application
Deploy a Custom Extensions in this SPACE SESSION
Inject the DAP script (eg, WalkMe, Pendo, Userpilot) into the session via Content Script
Activate the DAP - to be run from the Webfuse domain
Share the SPACE LINK with the DAP fully operation - no installation required.
With Webfuse, companies instantly activate their Digital Adoption Platform on any web application?even those they don?t own.Sales teams can now integrate guided workflows into Salesforce or HubSpot, even when they don?t have admin access to deploy scripts. HR & IT teams can roll out onboarding walkthroughs in Workday, ServiceNow, or SAP, reducing training time without waiting for vendor approval. Support teams can offer real-time, in-app assistance on third-party helpdesk platforms like Zendesk?without requiring browser extensions. Enterprises managing compliance & legacy systems can ensure users follow critical workflows in outdated applications, without modifying them.
```
## 
## Secure

### Participant Authentication and or Verification

By default, every session created in Webfuse is publicly accessible. However, you can enforce session authentication or user verification to restrict access to specific users. This can be accomplished by requiring participants to be 'registered' users within the Webfuse platform, or by delegating authentication to an external Identity Provider (IDP) through Single Sign-On (SSO).

In certain cases, you don't really want to restrict access to a certain application, you just want to make sure that the users are who they say they are. For this purpose you can also enable. Participant Identification.  A participant will then be required to provide their details (name, email) and you can optionally ask us to verify that the user is who they say they are.

```
? Use-case: Enable Zero Trust for Any Web Application
Organizations must enforce Zero-Trust security, ensuring only authenticated, authorized users can access applications?even those without built-in security controls. Traditional Zero-Trust setups require complex integrations with IdPs, VPNs, or gateways, making them costly and impractical for third-party or legacy apps.With Webfuse, businesses can instantly apply a Zero-Trust security layer to any web application without backend modifications. Using Virtual Web Sessions, Webfuse enforces authentication, access control, and session monitoring at the presentation layer?securing applications dynamically.
How It Works with Webfuse:
Create a Webfuse SPACE and  configure the STARTURL
Enforce Authentication on the SPACE - set to Members only
Add Space Members to the Space - optionally configure SSO
(Optionally) enable Session Monitoring
```
### Cookie Guard

The platform can be optionally configured  so that authentication cookies (HTTPonly cookies) will be protected from theft. The way this works is that the platform will encrypt each HTTPOnly cookie with a session specific strong and randomized key. This means that even when the cookie is obtained by an adversary, it cannot be used outside of the Webfuse session in which it has been created.

```
? Use-case: Prevent Session Hijacking & Session Cookie Theft
Logging into sensitive web applications (e.g., banking portals, enterprise dashboards, or government services) from untrusted devices?such as hotel business centers, public libraries, or internet caf?s?poses a serious security risk. Even with HTTPS encryption, session hijacking remains a threat due to:
Malware & Keyloggers ? Capturing login credentials and authentication tokens.
Cookie Theft ? Attackers extracting session cookies to impersonate users remotely.
Man-in-the-Middle (MitM) Attacks ? Intercepting authentication data over public Wi-Fi.
Once an attacker steals an authentication cookie, they can reuse it to gain unauthorized access?often without triggering additional authentication checks.With Webfuse?s Virtual Web Sessions & Cookie Guard, users can securely access sensitive web applications from untrusted devices without exposing persistent session cookies to threats. As authentication cookies are encrypted and tied exclusively to the Webfuse session. Once the Webfuse session ends, all session cookies become invalid. Even if an attacker extracts the cookie, they cannot replay it on another machine.
How it works with Webfuse:
Create a Webfuse SPACE and enable Cookie Guard
Any user who creates a Web Session from this SPACE can login to applications as usual, but now fully secured with the Webfuse Session.
Once completed and the Webfuse session ends, any Authentaction Cookies of the original application are instantly invalidated.
Even if an attacker has access to this cookie - it simply cannot be used
```
### 
### Additional Request and or Response Headers

The Custom Headers APP in Webfuse enables organizations to modify request and response headers dynamically, allowing for security enhancements, compliance enforcement, tracking control, and feature modifications?all without changing the underlying web application.

```
? Use-case: Adding Permission Policy to External Web Apps
Modern web browsers allow websites to request access to sensitive device features (e.g., camera, microphone, USB, Bluetooth). Malicious websites can exploit these permissions, tricking users into granting access.
You can add a specific Permission Policy header to each and every response obtained from the platform. With this you will be able to prevent a rogue script on a website from  accessing USB, Bluetooth devices or camera's. Or, maybe add a CSP header in combination with the Lockdown APP to prevent XSS attacks.
How it works with Webfuse:
Create a Webfuse SPACE
Open the Space Session
Install the Custom Headers APP
Add a Permission Policy Response Header set to: Permissions-Policy: camera=(), microphone=(), geolocation=()
```
### Lockdown APP** ADD-ON**

By default, virtual web sessions in Webfuse allow full access to the internet. However, you can restrict this by enabling URL restrictions through a grant list or a block list. This allows you to control which resources can be accessed within a session, enhancing security and compliance.

- **Grant List**: Limits access to a predefined list of allowed URLs. Any attempt to navigate outside this list results in an error, which can be customized.

- **Block List**: Opposite of the grant list, it restricts access to a list of disallowed URLs. This provides flexibility for administrators to control which sites can be accessed.

These URL restrictions can help manage security risks and ensure compliance with organizational policies.

```
? Use-case: Limit the Potential Impact of XSS Attacks
Cross-site scripting (XSS) attacks are often mitigated by setting content security policy (CSP) headers. However, if you cannot change the existing application, Webfuse's URL restrictions can be used to limit which domains are allowed within a virtual web session. This reduces the risk of XSS attacks by preventing the host browser from navigating to potentially malicious sites.
How it works with Webfuse:
Create a Webfuse SPACE
Set the Start URL to the specific application you want to protect, eg: https://example.com
Then add the Lockdown APP and configure it
Configure the ALLOWLIST to only allow request to *.example.com
Then share or embed the Space LINK
Anyone who then opens the session will open example.com, but even if that website has been compromised by rogue code, Webfuse will make sure that this application can not make any request to share information outside of example.com.
```
## 
## Observe

### *Web Session* Audit Logs

When enabling the audit functionality it is possible to gather deep session insights and fully understand what has happened during a session. For example, *where did the user navigate to? how long did he stay on that page? where forms changed? buttons clicked? tabs opened and or closed? *All these types of events will be collected as a ?human readable JSON log? on a data endpoint of your choice.

```
? Use-case: Enforcing Compliance with Webfuse Audit Logs
Regulated industries must ensure full transparency, accountability, and auditability of user interactions within critical web applications. However, many third-party SaaS platforms, legacy systems, and cloud applications lack built-in compliance logging, making it difficult to track: Who accessed what data and when? What changes were made to records? Were security policies and compliance requirements followed?
Organizations operating under strict regulatory frameworks?such as GDPR (privacy), HIPAA (healthcare), SOC 2 / ISO 27001 (security), and FINRA / SOX (financial compliance)?must maintain detailed logs of all user activities for audits, forensic investigations, and risk mitigation. 
By integrating Webfuse Virtual Web Sessions & Audit Logs, businesses can instantly enforce compliance monitoring without modifying the underlying application.
How it works with Webfuse:
Create  a Webfuse SPACE
Open the Space Session Editor
Install the Storage APP
And configure a custom S3 Storage End-Point
Install the Auditlog APP and point it to your custom S3 Endpoint
After this, every session created through this SPACE will create a custom JSON formatted audit log for that particular session collecting all important events during that session in an immutable log file. 
```
### *Session* Recording

Webfuse Session Recording captures a full, pixel-perfect playback of all user interactions within a Virtual Web Session. Unlike traditional event-based logging, this video-based session tracking provides unmatched visibility into user behavior, compliance monitoring, fraud detection, training, and security forensics; this video can then be stored on a data-endpoint of your choice.

```
? Use-case: Identifying UX Pain Points 
Traditional analytics tools like Google Analytics, Mixpanel, or heatmaps only provide surface-level insights into user behavior?tracking clicks, page views, and time spent. However, they fail to capture real frustration points, such as:
Where users hesitate before clicking (uncertainty or confusion).
Where they repeatedly click or rage-click (broken elements, unclear navigation).
Where they abandon a form mid-way (complexity, lack of trust, or unclear instructions).
Without visual context, UX designers and product teams struggle to understand WHY users drop off during key workflows.
With Webfuse Session Recording,teams gain a clear, visual understanding of how users interact with an application?seeing what users experience, even on third-party elements such as embedded payment providers (which other solutions generally fail to capture). 
How it works with Webfuse:
Create a Webfuse SPACE
Open the Space Session Editor
Configure a Storage Endpoint 
Install the Recording APP and point it to your storage end point
Share the SPACE Link with people whose session you'd like to record.
(Optionally) configure a START PAGE and or LANDING PAGE to provide instructions or ask to the participant to agree to your Terms of Service.

```
### Content Masking

Webfuse Content Masking is a privacy-first security layer that dynamically hides, redacts, or obfuscates sensitive information in real-time within a Virtual Web Session. It operates at the presentation layer, meaning that masking is enforced without modifying the original web application.

Webfuse uses CSS selectors to define which parts of a webpage should be masked. Once a masking rule is applied, Webfuse ensures that the data is:

- Other session participants will see either a blurred field, asterisks, or a complete redaction.  (See shared sessions)

- The Webfuse Automation API (read_dom, take_screenshot, get_elements) will return masked values instead of real data. (See Automation)

- Is excluded from audit logs and session recordings, ensuring compliance - Masked data is never stored or logged, ensuring compliance with privacy regulations like GDPR, HIPAA, and SOC2.

```
? Use-case: HIPAA compliant Session Recording
In the healthcare industry, telehealth providers, patient support teams, and healthcare insurers need to record online interactions for compliance, training, and quality assurance. However, traditional session recording solutions create compliance risks under HIPAA (Health Insurance Portability and Accountability Act), as they may: Capture Protected Health Information (PHI) without proper controls.   Without a HIPAA-compliant recording solution, healthcare providers risk non-compliance, privacy violations, and potential fines.

Webfuse enables secure, policy-driven session recording that ensures PHI remains protected while maintaining a complete record of interactions. By combining Content Masking, Granular Access Control, and Encrypted Storage, Webfuse provides a fully HIPAA-compliant session recording system.
How it works with Webfuse:
Create a Webfuse SPACE
Open the Space Session Editor
Set the Start URL to the Healthcare Web APP - you'd like to record
Install the Recorder APP
Configure a Custom Storage Endpoint
Install the Content Masking APP
Share the Space Link
```
## Collaborate

### Session* *Sharing

Webfuse allows sessions to be shared in real time, enabling a fully collaborative experience where multiple participants can view and interact with a live session. When Session Sharing is enabled in a SPACE, all participants can see the actions performed by the tab owner, fostering seamless collaboration, training, and co-browsing.

Enabling Session Sharing activates the Participant Panel, displaying all active users and their roles. Additionally, each Virtual Tab will indicate its owner, making it easy to track who is controlling the session.

By default, each SPACE generates a unique session per user. However, for persistent collaboration?such as recurring meetings, training sessions, or ongoing support workflows?Webfuse allows you to enable the SESSION_LINK_MODE  option, effectively turning the SPACE Link  into a Permanent Meeting Link.

In shared sessions, Webfuse allows for real-time control switching between participants. The Host can grant control to another user, allowing them to interact with the web session as if it were their own. This is particularly useful for remote support, guided walkthroughs, and collaborative work environments.

- **User Roles and Permissions**: Describe the granularity of control over user permissions and roles within a shared session. There are different user roles, including **Participant, Space Admin, Tab Owner, and Host**. Space Admins can control session settings, manage participants, and modify session properties, while a Host ensures continuity in shared sessions.

- **Collaborative Tools and Interfaces**: Webfuse includes a **Participant Panel** for managing users, a **Communication Panel** for real-time chat and video conferencing, and the ability to share tabs across users.

- **Presenter Mode:** A single participant (Host) controls the session, and others can only view.

- **Interactive Mode:** Participants can switch control among themselves, promoting real-time collaboration.

- **Role-Based Switching:** Space Admins can enforce control policies based on user roles.

With Session Sharing, Webfuse transforms any web application into a real-time, multi-user environment, removing barriers to collaboration, guidance, and support?all without modifying the original platform.

```
? Use-case: High-Performance, Low-Latency Webinars with Webfuse Session Sharing
Traditional screen sharing solutions share content as a stream of pixels, which often results in lag, compression artifacts, and low frame rates?especially when presenting dynamic content like Google Slides, Office365 PowerPoint, or interactive dashboards. Participants experience blurry text, stuttering animations, and delays, making real-time collaboration difficult.
Webfuse delivers real-time, high-fidelity session sharing by transmitting the actual DOM (Document Object Model) of the web application?not a pixel-based video stream. This enables instant interactions, crisp visuals, and ultra-low latency across an unlimited number of participants.
You can embed this functionality in your own webinar / web sharing technology by offering high quality screen sharing of any web content. 
How it works with Webfuse:
Create a Webfuse SPACE
Enable 'SESSION SHARING
Open the SPACE SESSION
Within the session OPEN THE CONTENT you'd  like to share
Invite any other participant to the session by sharing the SPACE SESSION LINK
This  results in a HIGH QUALITY web session that can be shared with multiple participants. This can optionally be automated leveraging our APIs to enable seamless integration with other platforms.
```
Webfuse offers two primary **collaborative modes**:

- **Single  ****Presenter Mode****:** A single Host dictates what other participants see and interact with. If the Host leaves, the session ends.

- **Multi Presenter Mode:** All participants can freely navigate, open tabs, and follow each other's views.

These modes ensure flexibility for different use cases, from webinar-style presentations to interactive, peer-driven collaboration.

```
? Use-case: Convert any Web Application into a Fully Collaborative App
The Webinar Use-Case previously listed is great for outbound sessions or programmatic integrations. But it is also very easy to take any existing web application and then convert this into a collaborative environment. For example, assume that you and your team mates have a weekly project meeting where you will need to discuss the project which is listed in an Asana Board and where some other documents are project documentation is on Notion. With Webfuse you can easily convert this into a weekly recurring meeting where the content is automatically opened and shared. 
How it works with Webfuse:
Create a Webfuse SPACE
Set the option MAINTAIN_SPACE_LINK so that the link will not change to a unique SPACE SESSION LINK every time
Add all the project participants as MEMBERS to the SPACE
Open the SPACE SESSION CONFIGURATION
Configure the START URL to open the project links (Asana, Figma, Notion, etc.)
Allow all SPACE MEMBERS to HOST the Session
Add the SPACE LINK to a recurring calendar invite
Now every week you will be able to quickly jump into a collaborative session where all project documentation will already be opened for you and where you can share the content without any loss of quality.
```
### Video Calling

Webfuse integrates a built-in **Video Calling App** that enables real-time audio and video communication within sessions. Features include:

- **End-to-End Encryption:** Ensuring secure conversations.

- **Multi-Participant Support:** Video calls can include multiple users simultaneously.

- **Screen Sharing:** Participants can share their screens for enhanced collaboration.

- **Floating Video Interface:** Allows seamless interaction with web content while keeping video conversations active.

These collaborative functionalities make Webfuse a powerful tool for **virtual meetings, remote support, and live collaboration on web applications**.

```
? Use-case: Real-Time Expert Guidance in Enterprise SaaS Apps
A software company offers a premium onboarding experience where new users receive real-time guidance from a live expert while navigating the software.
How it works with Webfuse:
Create a Webfuse SPACE
Add all the project participants as MEMBERS to the SPACE
Setup a custom Landingpage with details that by clicking 'go' you will be connected to a real agent that will be able to support you with your Salesforce Setup.
Enable Queue functionality
Open the SPACE SESSION CONFIGURATION
Configure the START URL to open your app (eg SalesForce)
Allow all SPACE MEMBERS to HOST the Session
Install the Videochat APP
Configure the APP to Auto Start Video
And enable the Videochat Prompt
Add the SPACE LINK to a recurring calendar invite
Instruct the agent to watch the Queue for incoming requests.
With the above setup, every user that will navigate to the Landingpage will automatically queue a request that can be answered by any of your Video Call Support agents to assist the user.
```
## Automate

### Automation API

The rise of Agent AI?including OpenAI?s Operator, Claude?s Computer Use API, and Google?s Project Mariner?has redefined how AI interacts with digital environments. These AI-driven agents can now see, reason, and take action on live interfaces, bridging the gap between automation and real-world usability.

But these AI models are often trapped within their own environments, restricted to controlled sandboxes, API integrations, or scripted automation that fails when dealing with real, dynamic web applications. Traditional automation methods require custom vendor integrations, remote browser workarounds, or closed ecosystems that limit deployment flexibility.

Webfuse breaks down these barriers by enabling Agent AI to operate directly on any website, accessible from a simple web link. Instead of being confined to proprietary AI environments or limited to backend-controlled workflows, Webfuse provides a fully interactive automation layer that:

- Works on any web application without requiring backend integration or vendor approval.

- Creates a fully AI-driven experience, where agents can see, interact, and modify web apps in real-time.

- Makes AI-driven automation instantly deployable, turning any website into an AI-powered experience?without disrupting its original functionality.

With Webfuse's Automation API, AI agents can:

- Perceive the web environment ? Extract real-time DOM data with read_dom(), capture live UI changes, and take full-page screenshots (take_screenshot()).

- Interact like a human ? Click buttons, fill forms, navigate pages, and control UI elements dynamically with click(), mousemove(), type(), and scroll().

- Enhance & modify applications ? Inject custom logic and UI elements using Webfuse Extensions, enabling AI-driven overlays, contextual guidance, and adaptive automation.

```
? Use-case: AI-Powered Life Insurance Assistance with Webfuse
Life insurance policies are often complex and difficult to navigate, leading to high drop-off rates during the application process. Customers struggle with understanding policy options, eligibility criteria, and required documentation, which results in abandoned applications and missed sales opportunities.
With Webfuse, insurers can embed an AI-powered assistant directly into their public website (e.g., lifeinsurance.com/ai-assist), enabling real-time guidance for prospective customers.
How It Works with Webfuse:
Create a SPACE ? Define a controlled Webfuse environment.
Create a custom landing page which explains what will happen
Open a Space Session
Open the Space Session Editor
Set the start URL to the Insurance Portal
Install a Custom Extension
This custom extension can load its logic in background.js which will run all logic in a webwork
This script can then make calls using our Automation API in order to take screenshots and or actions
Set the START PAGE ? Point it to the Insurance Portal
Install a Custom Extenions
Enable ACCESS CONTROL ? Restrict access based on authentication rules.
Enforce Session Limits ? Use the REST API to define time-based access or embed a Virtual Web Session Extension to dynamically control session expiration.
? Outcome: Now a single Webfuse space has augmented an existing Insurance portal with a full-blown AI assistant. Combine this with other functionality, such as offloading the session to agents where needed
```
## 
### Virtual Participant Functionality

As AI-driven automation evolves, businesses and developers need more than just API-based control?they require a flexible, interactive, and secure way to automate workflows without compromising security or usability.

Webfuse?s Virtual Participant introduces a groundbreaking capability: the ability to add an AI-driven remote browser as a session participant, allowing secure, interactive, and isolated automation. Unlike traditional automation that runs directly on the user?s machine, this method ensures stronger security, better collaboration, and fully isolated execution environments.

Key Capabilities of Virtual Participant

1. **Isolated AI Execution for Secure API Calls** \
 Traditional browser automation exposes API keys when executed on a user?s machine, creating security risks. With Virtual Participant, automation tasks run inside an isolated Webfuse instance, protecting sensitive API credentials while allowing secure interactions with external endpoints.

2. **Real-Time Human + AI Collaboration** \
 Because the Virtual Participant is an actual session participant, it can interact with real users in the same session. This enables:

1. Chat-based assistance where AI and human users collaborate on content.

2. On-screen annotations to guide users without modifying the actual web application.

3. Masked data interactions, ensuring that sensitive user inputs (e.g., personal details) are hidden from the AI agent.

3. **Fully Automated Web Actions Without a Human User** \
 In some cases, an AI-driven Virtual Participant can operate independently, executing full end-to-end workflows inside a Webfuse Virtual Web Session. This enables:

4. Automated data entry and retrieval (e.g., an AI filling forms, submitting reports, or extracting information).

5. Automated compliance monitoring, ensuring websites adhere to policies and regulations without human intervention.

6. AI-driven regression testing, where a Virtual Participant repeatedly interacts with a website to test functionality.

# 

# Technical Architecture

## System Architecture

![](/images/bKy_Image_3.png)

Webfuse's Augmentation Platform is hosted across the world in multiple data centers. To optimize performance, we will make sure that the user by default is always connected to the nearest geographically located server. Thereby, the Webfuse platform will act as an automatically adapting content delivery network, similar to how for example Akamai, CloudFlare are operating, except no special setup is required.

The virtual session will run through Webfuse, which means that while the user's browser will connect to the Webfuse servers, the user will never connect directly to the original application. Webfuse will act as both a forwarding and reverse proxy in-one.

![](/images/slK_Image_4.png)

The virtual session can be used as a regular browser session. Newly created tabs within the session will be created as *virtual tabs* and will live within the virtual session. Also visually they are represented as a visible virtual tab within the existing browsing context.

When a request is made from a user to an origin server, it first passes through the Webfuse platform. During this process, Webfuse adds additional headers to each request, providing useful information about the requestor's identity and allowing requests to be linked back to a Webfuse session. Below are the headers added by Webfuse and their respective descriptions.

These additional headers provide transparency and traceability when dealing with Webfuse virtual sessions. They can help ensure secure communication and enable backend systems to validate the authenticity of requests. Additionally, you can through the HEADERS APP add additional request or response headers.

| Header | Description | Example |
|---|---|---|
| Surfly-Forwarded | This request header contains the IP address of the original requester. It retains the original 'forwarded-for' header and can be either an IPv4 or IPv6 address. This information is useful for tracking the source of the request. | ::ffff:127.0.0.1 |
| X-Surfly-Sessionid | This request header uniquely identifies the Webfuse session. It can be used by the target application to verify that a request originated from Webfuse. To ensure the authenticity of the session, verify the session ID with a REST call to the Webfuse server. | f50zXqx3p1UZQQSknH4qdkjABg |
| Surfly-Proxy-Metrics | This response header provides detailed timing information about various stages of processing a request in the platform. | req_read: 5, resp_read: 10, decomp: 2, decode: 3, detect_akamai: 1, chardet: 1, html: 20, css: -, js: -, rstr: 2, t: 59 |

## Content Rewriting and Modification

At the core of our solution lies the **content-rewriting proxy**. It is a full-featured HTTPS and WebSocket proxy that is able to handle traffic from any modern web application. It parses and modifies the traffic on the fly in such a way that all subsequent traffic is routed through the proxy. This means, among other things, that all the links on the served pages are rewritten, so they point to proxied versions of the target URLs.

But that?s just a part of the story. Anyone familiar with web server rewriting modules (such as ARR in IIS or mod_rewrite in Apache) knows that having rewrite rules inside the HTTP proxy is just not enough. Modern web apps rely on Javascript, so most of the content is actually generated on the client side. For example, the code below would create a link that is virtually impossible to capture by the proxy:

`const`` ``currentDate`` ``=`` ``new`` ``Date``();`` \
``const`` ``link`` ``=`` ``document.createElement(``'a'``);`
```
//At the time of writing, this would generate a link to https://the-year-2025.test`link.href`` ``=`` ``'https://the-year-'`` ``+`` ``currentDate.getFullYear()`` ``+`` ``'.test'``;`
document.body.appendChild(link);
```
Moreover, the Javascript code itself could be dynamically generated:

`let`` ``foo`` ``=`` ``{};`` \
``const`` ``code`` ``=`` ``'foo.href = "//example.com"'``;`` \
``eval``(code);`` ``//this will not do anything`
`foo`` ``=`` ``window.location;`` \
``eval``(code);``  //this time the page will navigate to example.com`

And if that is not enough, the code could be obfuscated. This code does exactly the same as the one above:

`const`` ``_0x5c2c=[``'foo.href\x20=\x20\x22//example.com\x22'``,``'703271gmlQyD'``,``'381497emYCfi'``,`
`'1019923hJJvMQ'``,``'603QLrHWo'``,``'383617OfWLUT'``,``'location'``,``'1177365yPaujx'``,`
`'1559GDizPw'``,``'648076JfmmxG'``];``const`` ``_0x34f2=``function``(_0x11440c,_0x3244b0){_0x11440c=_0x11440c-0x17d;``let`` ``_0x5c2cf2=_0x5c2c[_0x11440c];``return`` ``_0x5c2cf2;};``const`` ``_0x452fd3=_0x34f2;(``function``(_0x4f836c,_0xafd59a){``const`` ``_0x5094f6=_0x34f2;``while``(!![]){``try``{``const`` ``_0x516045=``parseInt``(_0x5094f6(``0x185``))+-parseInt(_0x5094f6(``0x183``))+-parseInt(_0x5094f6(``0x17f``))+``parseInt``(_0x5094f6(``0x181``))+-parseInt(_0x5094f6(``0x186``))*-parseInt(_0x5094f6(``0x180``))+-parseInt(_0x5094f6(``0x184``))+``parseInt``(_0x5094f6(``0x17d``));``if``(_0x516045===_0xafd59a)``break``;``else`` ``_0x4f836c[``'push'``](_0x4f836c[``'shift'``]());}``catch``(_0x8adaf){_0x4f836c[``'push'``](_0x4f836c[``'shift'``]());}}}(_0x5c2c,``0xb21d8``));``let`` ``foo={};``const`` ``code=_0x452fd3(``0x182``);``eval``(code),foo=window[_0x452fd3(``0x17e``)],``eval``(code);`

In order to handle these and other tricky cases, we?ve built a full **Javascript sandbox**. This allows us to apply custom wrapper functions to all execution points, such as function calls and object property access. These wrappers are executed in runtime inside the browser, so it allows us to intercept all relevant Web API requests and change the return value before giving it back to the application code.

Together, the Javascript sandbox and the network proxy can practically capture all inputs and outputs of any web application, forming together the ingredient of **the virtual web session** that a user will experience in its browser, where all the resulting changes will be rendered locally.  

## 
## Security & Privacy

Webfuse is built with security and privacy at its core, ensuring that all interactions within a Virtual Web Session remain isolated, secure, and compliant. Unlike traditional web augmentation solutions that rely on cloud-based rendering or remote execution, Webfuse ensures that all content is rendered locally on the user's device, eliminating unnecessary exposure to third-party servers.

### Key Security & Privacy Features

- **Everything is Locally Rendered**

- Webfuse operates directly within the user's browser, meaning **no content is streamed or processed remotely**.

- This prevents **third-party interception** of sensitive web interactions.

- **No Session Data is Stored by Default**

- By design, Webfuse does **not persist session data, cookies, or browsing history** beyond the active session.

- Once a session ends, **all temporary data is erased**, ensuring **zero residual exposure**.

- **Bring Your Own Storage (Optional)**

- For organizations that require **audit logging, session recording, or compliance tracking**, Webfuse allows **full control over data storage**.

- Companies can **configure their own secure storage endpoints** (e.g., AWS S3, on-premise storage) to retain logs **without relying on third-party servers**.

- **Enterprise-Grade Compliance & Certifications**

- **ISO 27001 Certified** ? Webfuse follows **international best practices** for information security management.

- **SOC 2 Audit Report Available** ? Ensuring **transparency, integrity, and security** of data handling processes.

Webfuse?s privacy-first architecture ensures that organizations retain full control over their data, eliminating reliance on third-party storage while maintaining compliance with GDPR, HIPAA, and other regulatory frameworks. By rendering everything locally on the user's device and storing no session data by default, Webfuse minimizes the attack surface and prevents unauthorized access to sensitive information. For businesses requiring audit logs or session recordings, Webfuse allows full flexibility to use their own secure storage endpoints, avoiding vendor lock-in while ensuring data sovereignty and enterprise-grade security.

|  |  |  |  |
|---|---|---|---|

# Integrating Webfuse 

Although Studio is an excellent tool for creating sessions, you will likely want to integrate the session space into your own application and/or add features in many instances. Our range of APIs can help you achieve this.

## Session Creation

To create new SPACE SESSIONS, use the REST API endpoint associated with your Webfuse SPACE. In the example below, we establish a virtual session on a predefined space named ?https://[company.webfuse.com/+embed](https://www.google.com/search?q=https://company.webfuse.com/+embed)?

`curl`` ``-X`` ``GET`` ``"https://company.webfuse.com/+embed/"`` ``\`` \
  ``-H`` ``"Authorization: Token rk_your_space_rest_key"`` ``\`` \
  ``-H`` ``"Content-Type: application/json"`

The Webfuse Platform will respond with a JSON object which will contain a SPACE SESSION LINK.

BLANK_LINE_FOUND_IN_GOOGLE_DOCS_2MD_PRO`{`` ``"link":"``https://webfuse.com/s20I22gcoJnWQziuXaxU3hqNtA``",`
```
  "session_id":"s20I22gcoJnWQziuXaxU3hqNtA"}

After the link is opened, the user will join the SPACE and view it as it was configured in STUDIO, including any APPS or extension configurations. Before joining, the user's access rights will be checked, and the user will be verified if needed. Then, the user will join the space session and open any pre-defined START URLs.

```
If this is a SHARED space, then the link can be opened by multiple users to create a collaborative experience.

## Magic Link Functionality

While a SPACE SESSION LINK is used for all participants, a MAGIC LINK provides additional flexibility and customization options for individual participants, including the ability to bypass SPACE security settings.

You can do this as follows:

`import`` ``jwt`
`import`` ``datetime`
BLANK_LINE_FOUND_IN_GOOGLE_DOCS_2MD_PROUse your actual REST key (starts with rk_)`REST_KEY`` ``=`` ``"rk_your_space_rest_key"`
BLANK_LINE_FOUND_IN_GOOGLE_DOCS_2MD_PROConfigure the personal parameters`payload`` ``=`` ``{`
`	``"space_id"``:`` ``"embed"``,`
`	``"name"``:`` ``"John Doe"``,`
`	``"can_host"``:`` ``True`
```
}`token`` ``=`` ``jwt.encode(payload,`` ``REST_KEY,`` ``algorithm=``"HS256"``)`
`URL`` ``=`` ``f"https://webfuse.com/s20I22gcoJnWQziuXaxU3hqNtA?magic_link={token}"`

```
When you then give the URL to a certain participant they will be able to join the SPACE as a verified user, bypassing any authentication and or verification settings that might be in-place.

## Embedding Webfuse Sessions - **Widget API**

The Widget API can be used to embed a SPACE session into your own web application or website. This API will handle the creation of the iFrame and session link and provide you with an API to control the session itself, including switching tabs, opening URLs, and enabling/disabling features like the video camera and microphone. Additionally, you can use the API to listen for session events, such as participants joining or URLs being opened. The Widget API allows you to build an external interface around the embedded Webfuse SPACE session and create interaction buttons or logic to change the session's behavior.

The below example will show how to embed a SPACE session into a web application and then how you can programmatically interface with that session.

`<iframe id=``"sessionContainer"`` style=``"width:100%; height:600px; border:1px solid #ccc;"``></iframe>`
`<input id=``"urlInput"`` placeholder=``"Enter a URL..."`` style=``"width:300px; margin-top:10px;"``>`
`<button onclick=``"openTab()"``>Go</button>`
BLANK_LINE_FOUND_IN_GOOGLE_DOCS_2MD_PRO```
<script>`  (``function``(w,e,b,f,u,s){w[f]=w[f]||{initSpace:()=>``new`` ``Promise``(r=>{w[f].q=``arguments``;w[f].resolve=r})};`
`	u=e.createElement(b);s=e.getElementsByTagName(b)[``0``];u.``async``=``1``;u.src=``'https://surfly.online/surfly.js'``;`
	s.parentNode.insertBefore(u,s);`  })(window,document,``'script'``,``'Webfuse'``);`
`  ``let`` session;`
`  window.onload = ``async`` () => {`
`	``const`` space = ``await`` Webfuse.initSpace(``'WIDGET_KEY'``,`` 'SPACE_ID'``, {});`
	session = space.session();`	``await`` session.start(``'#sessionContainer'``);`
  };`  ``function`` openTab() {`
`	``const`` url = document.getElementById(``'urlInput'``).value;`
`	``if`` (session && url) session.openTab(url);`
`	``else`` alert(``'Enter a valid URL or wait for the session to start.'``);`
  }</script>
```
Make sure to change the WIDGET_KEY and SPACE_ID with the correct and actual values.

## Extending Functionality - **Extensions API**

The Webfuse **Extension API** enables developers to extend, customize, and automate behavior within Virtual Web Sessions by injecting modular JavaScript packages?similar to browser extensions. These **Webfuse Extensions** allow fine-grained control over the augmented web experience, enabling advanced UI modifications, automation flows, analytics hooks, or user interface overlays.

Webfuse Extensions follow the familiar structure of the **Browser Extension API**, making it easy for developers with experience in Chrome or Firefox extensions to onboard quickly. Each extension consists of one or more standard components:

- **Background Scripts**: Persistent logic that handles events, timers, or stateful data across tabs. \


- **Content Scripts**: Injected directly into the augmented web page?s DOM, used to manipulate UI, listen to events, or extract data. \


- **Popup UIs** (optional): Custom interfaces triggered from the session toolbar, useful for launching actions or collecting user input. \


Each extension is defined through a `manifest.json` file, which declares metadata, permissions, script files, and UI components. This modular architecture makes it easy to package, share, and reuse extensions across different SPACES.

By combining real-time DOM control with secure sandboxing inside the Webfuse session environment, the Extension API offers a powerful way to embed business logic, assistive tools, or automation workflows?without modifying the underlying application.

For example, the following extension will highlight all Headings on the page:

`document.addEventListener(``"DOMContentLoaded"``,`` ``highlightHeadings);`
`function`` ``highlightHeadings()`` ``{`
`  ``document.querySelectorAll(``'h1'``).forEach(el`` ``=>`` ``{`
`	``el.style.backgroundColor`` ``=`` ``'#fffb91'``;`
`	``el.style.border`` ``=`` ``'2px dashed #f0c000'``;`
`  ``});`
```
}
```
This can be configured with the following Manifest.JSON file:

```
{`  ``"name"``: ``"Highlight Headings"``,`
`  ``"description"``: ``"A simple extension that highlights all H1 headers on the page."``,`
`  ``"version"``: ``"1.0.0"``,`
`  ``"manifest_version"``: ``2``,`
`  ``"content_scripts"``: [`
	{`  	``"matches"``: [``"<all_urls>"``],`
`  	``"js"``: [``"content.js"``]`
	}  ],`  ``"permissions"``: [],`
`  ``"webfuse_specific"``: {`
`	``"display_name"``: ``"Highlight H1s"``,`
`	``"icon"``: ``"icon.png"`
  }}

Automating Actions - **Automation API**


Webfuse Automation API empowers developers to simulate real user interactions on any web application without requiring access to its source code. By merging Webfuse's Virtual Web Session with high-level automation primitives, developers can manage complex web workflows that imitate the behavior of a human operator. This capability makes Webfuse a strong substitute for traditional RPA tools, particularly in settings where browser automation is limited or integration is hindered by technical or organizational barriers.

Unlike browser extensions or remote virtual browsers, Webfuse automation occurs within a secure, sandboxed Virtual Tab and doesn't rely on unstable DOM scraping or runtime injection into uncontrolled codebases. Instead, developers gain programmatic control over sessions using straightforward JavaScript commands that simulate user behavior at the presentation layer?moving the mouse, clicking, typing, scrolling, and waiting.

```
Whether you're developing AI agents that navigate enterprise tools, automating customer onboarding workflows, or testing legacy portals without exposed APIs, Webfuse allows you to interact with any web UI like an actual user.

The `browser.virtualSession.automation` namespace is available inside Webfuse session extensions, offering these fundamental commands:

- wait(ms)

- moveMouse(x,y)

- click(selector)

- scroll(amount, direction, [selector])

- type(text, [selector])

- read_dom([selector])

- take_screenshot()

For example, the following snippet can automate a login form:

`await`` ``browser.virtualSession.automation.wait(``500``);`
`await`` ``browser.virtualSession.automation.type(``'username123'``,`` ``'#username'``);`
`await`` ``browser.virtualSession.automation.type(``'secureP@ssword!'``,`` ``'#password'``);`
`await`` ``browser.virtualSession.automation.click(``'#login-button'``);`

Automation commands are natively available inside Webfuse Session Extensions, meaning no external dependencies are required. You can bundle automation scripts as part of your custom extensions or trigger them dynamically in response to events (e.g., `session_started`) using the Extension API.

The Webfuse Automation API is designed to work seamlessly with agentic tools such as: Anthropic's[ ](https://docs.anthropic.com/en/docs/agents-and-tools/computer-use#computer-tool)[Computer Use API](https://docs.anthropic.com/en/docs/agents-and-tools/computer-use#computer-tool), OpenAI?s[ ](https://platform.openai.com/docs/guides/function-calling)[Function Calling](https://platform.openai.com/docs/guides/function-calling), Custom LLM pipelines for autonomous agents \


This allows developers to embed intelligent behavior into any web application without needing to build custom integrations or browser plugins.

## 
## Virtualized Participant

A Virtualized Participant is essentially a headless, programmable browser agent that joins a Webfuse session just like a human user would?but it's controlled entirely via code or an external system.

Think of it as a  browser-based robot that behaves like a real participant, interacts with the UI, follows or leads navigation, and can even co-browse or collaborate?all inside a secure, isolated virtual tab.

It?s not a browser extension. It?s not Selenium. It?s not Puppeteer. It?s not a remote desktop.

It?s a full-fledged, session-level entity that can:

- Navigate web apps visually

- Click, scroll, type, or interact with the DOM

- Observe other participants? actions

- Join huddle or presenter sessions

- Switch control roles dynamically

- Receive session events and trigger session actions

- Collaborate with or hand off control to or from humans

In order to enable the virtual participant, one simply needs to install the Virtual Participant APP and then configure an extension to only load on this participant by setting the flag `virtualized_browser_only` to `True` in the Manifest.JSON

```
{`  ``"manifest_version"``:`` ``3``,`
`  ``"name"``:`` ``"Claude Agent Assistant"``,`
`  ``"version"``:`` ``"1.0.0"``,`
`  ``"description"``:`` ``"LLM-powered virtual participant using Automation API."``,`
`  ``"action"``:`` ``{`` ``"default_popup"``:`` ``"popup.html"`` ``},`
`  ``"background"``:`` ``{`` ``"service_worker"``:`` ``"background.js"`` ``},`
`  ``"content_scripts"``:`` ``[`
`	``{`` ``"matches"``:`` ``[``"<all_urls>"``],`` ``"js"``:`` ``[``"content.js"``]`` ``}`
`  ``],`
`  ``"host_permissions"``:`` ``[``"<all_urls>"``],`
`  ``"chrome_url_overrides"``:`` ``{`` ``"newtab"``:`` ``"newtab.html"`` ``},`
`  ``"virtualized_browser_only"``:`` ``true,`
`  ``"env"``:`` ``[`
`	``{`` ``"key"``:`` ``"AGENT_MODE"``,`` ``"value"``:`` ``"claude"`` ``},`
`	``{`` ``"key"``:`` ``"API_PROXY_URL"``,`` ``"value"``:`` ``"https://your-server.com/api/llm"`` ``}`
`  ``]`
}
