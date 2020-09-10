
![SuperTokens banner](https://raw.githubusercontent.com/supertokens/supertokens-logo/master/images/Artboard%20%E2%80%93%2027%402x.png)

# SuperTokens

<a href="https://supertokens.io/discord">
<img src="https://img.shields.io/discord/603466164219281420.svg?logo=discord"
    alt="chat on Discord"></a>

## Table of Contents
- [🚀 What is SuperTokens?](https://github.com/supertokens/supertokens-core#what-is-supertokens)
    - [Philosophy](https://github.com/supertokens/supertokens-core#philosophy)
    - [Features](https://github.com/supertokens/supertokens-core#features)
    - [Documentation](https://github.com/supertokens/supertokens-core#documentation)
- [🏗️ Architecture](https://github.com/supertokens/supertokens-core#architecture)
- [🔥 SuperTokens vs Others](https://github.com/supertokens/supertokens-core#supertokens-vs-others)
- [💵 How will we make money?](https://github.com/supertokens/supertokens-core#how-will-we-make-money)
    - [Backers](https://github.com/supertokens/supertokens-core#backers)
- [☕ Why Java?](https://github.com/supertokens/supertokens-core#why-java)
- [🛠️ Building from source](https://github.com/supertokens/supertokens-core#building-from-source)
- [👥 Community](https://github.com/supertokens/supertokens-core#community)
    - [Contributors](https://github.com/supertokens/supertokens-core#contributors)
- [👩‍💻 Contributing](https://github.com/supertokens/supertokens-core#contributing)
- [📜 Development history](https://github.com/supertokens/supertokens-core#development-history)
- [📝 License](https://github.com/supertokens/supertokens-core#license)

If you like our project, please :star2: this repository! For feedback, feel free to join our [Discord](https://supertokens.io/discord), or create an issue on this repo

## What is SuperTokens?
SuperTokens is an open core alternative to proprietary login providers like Auth0 or AWS Cognito. We are
 different because we offer:
- Open source: SuperTokens can be used for free, forever, with no limits.
- An on prem deployment with no connection to our servers. You control 100% of your user data.
- An end to end solution with login, sign ups, user and session management, without all the complexities of OAuth protocols.
- Ease of implementation and higher security
- Extensibility: Anyone can contribute and make SuperTokens better!

### Philosophy
Authentication directly affects UX, dev experience and security of any app. We believe that
 current solutions are unable to optimise for all three "pillars", leading to a large number of
  applications hand rolling their own auth. This not only leads to security issues, but is also a massive
   time drain.
  
We want to change that - we believe the only way is to provide a solution that has the right level of
 abstraction, gives you maximum control, is secure, and is simple to use - just like if you build it yourself,
  from scratch (minus the time to learn, build and maintain).

### Features
- Login (coming soon):
    - A decoupled login & sign up form as React components - pretty by default, but fully customisable.
    - Email & password login with email verification, and forgot password flows
    - Extensibility to build other methods of login - for example passwordless login.
    - Extensibility to chain various login challenges
    - Password management - hashing + salting.
    - Social and other types of login
    - Other community requests...
<img src="https://raw.githubusercontent.com/supertokens/supertokens-logo/master/gifs/login-readme.gif" height="300px"/>

- Session management
    - Create, verify, refresh & revoke sessions.
    - Follows all session best practices like using `httpOnly` cookies.
    - Prevents common session vulnerabilities like session fixation, CSRF or brute force attacks.
    - Detects session hijacking using [rotating refresh tokens](https://youtu.be/6Vzit514kZY?t=547).
    - Optimal time and space complexity - session verifications < 1 MS
    - Automatic JWT signing key rotation, without logging users out
    - Ability to get all sessions given a user ID.
    - Reading session data on the frontend, securely.
    - Manipulation of session and JWT payloads
    - Other community requests...

- User management (coming soon)
    - (Un)banning & deleting users
    - Resetting user passwords
    - Associating users with roles
    - Login identity consolidation (if a user logs in via google and via twitter, with the same email, they are
     treated as the same user).
    - Other community requests...

### Documentation
As of now, we only offer session management.

The docs can be seen [here](https://supertokens.io/docs/pro/getting-started/installation)

A short [implementation video](https://www.youtube.com/watch?v=kbC-QzxeZ4s&feature=emb_logo)


## Architecture
We provide a fullstack solution:
- **Frontend SDK (React, iOS, Android etc)**: Provide a login / sign up UI, automatic refreshing of sessions
- **Backend SDK (NodeJS, Flask, Laravel etc)**: APIs to handle login, sign up and session management.
- **SuperTokens core (this repo)**: An http service that handles the bulk of operations handled by SuperTokens. The
 backend SDK is a minimal layer that makes it easy for you to interact with this service.
 - **Database plugins (MongoDB, MySQL etc)**: Is a JAR extension to the SuperTokens core, used to interface with the
  appropriate database.

The frontend SDK talks to your API layer, which uses the backend SDK.

The backend SDK talks to the SuperTokens core whenever necessary

SuperTokens core talks to the installed database plugin to store information in the database. It can be run on
 premise, with or without Docker. You can also use our managed service to run this.

## SuperTokens vs others

Please [contact us](mailto:team@supertokens.io) if any of the information listed below is incorrect.

|                                	|       SuperTokens <img src="https://avatars2.githubusercontent.com/u/50478857?s=200&v=4" alt="Supertokens Logo" width="30" height="30">     	|        Auth0 <img src="https://cdn.auth0.com/website/assets/pages/press/img/auth0-badge-5c9de7e409.svg" alt="Auth0 Logo" width="25" height="25">       	|     AWS Cognito <img src="https://m.media-amazon.com/images/G/01/mobile-apps/dex/login-with-amazon/Cognito-Logo._TTH_.png" alt="Cognito Logo" width="35" height="35">    	|      Keycloak <img src="https://dyltqmyl993wv.cloudfront.net/assets/stacks/keycloak-gatekeeper/img/keycloak-gatekeeper-stack-220x234.png" alt="Keycloak Logo" width="30" height="30">     	|     FusionAuth <img src="https://res-3.cloudinary.com/crunchbase-production/image/upload/c_lpad,h_256,w_256,f_auto,q_auto:eco/zvhuxc69smizw7a9gggx" alt="FusionAuth Logo" width="35" height="35">    	|    Firebase Auth</br> <img src="https://static.dribbble.com/users/528264/screenshots/3140440/firebase_logo.png" alt="Firebase Logo" width="30" height="30">   	|
|----------------------------------------	|:-----------------------:	|:------------------:	|:------------------:	|:------------------:	|:------------------:	|:------------------:	|
| Open source                            	|    :heavy_check_mark:   	|                    	|                    	| :heavy_check_mark: 	|                    	|                    	|
| On premise                             	|    :heavy_check_mark:   	|         :heavy_check_mark: [1]        	|                    	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	|
| Managed service                        	|    :heavy_check_mark:   	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	
| Managed service, with your database    	|       Coming Soon       	|                    	|                    	|                    	|                    	|                    	|                    	
| Use with serverless                    	|    :heavy_check_mark:   	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	
| Free for unlimited users               	|    :heavy_check_mark:   	|                    	|                    	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	|
| Ease of configuration                  	|    :heavy_check_mark:   	| :heavy_check_mark: 	|                    	|                    	| :heavy_check_mark: 	|                    	|                    	
| Support for distributed infra          	| :heavy_check_mark:  [2] 	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	|                    	| :heavy_check_mark: 	|                    	
| Database agnostic                      	|    :heavy_check_mark:   	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	|                    	| :heavy_check_mark: 	|                    	
| Customisable Login widget              	|       Coming soon       	| :heavy_check_mark: 	| :heavy_check_mark: 	| :heavy_check_mark: 	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	
| Unlimited Social Login                 	|       Coming soon       	|                    	|                    	| :heavy_check_mark: 	|                    	|                    	|                    	
| Role & Attribute based access  control 	|       Coming Soon       	| :heavy_check_mark: 	| :heavy_check_mark: 	| :heavy_check_mark: 	| :heavy_check_mark: 	| :heavy_check_mark: 	| 
| Sessions using cookies                 	|    :heavy_check_mark:   	|                    	|                    	|                    	|                    	|                    	|                    	
| Session hijacking detection            	|    :heavy_check_mark:   	|    :heavy_check_mark:   	|                    	|                    	|                    	|                    	|                    	
| No cloud lockin                        	|    :heavy_check_mark:   	| :heavy_check_mark: 	|                    	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	|
| Low feature lockin                        	|    :heavy_check_mark:   	|                    	|                    	|                    	|                    	|                    	|
| Dedicated Support                      	|    :heavy_check_mark:   	| :heavy_check_mark: 	| :heavy_check_mark: 	|                    	| :heavy_check_mark: 	| :heavy_check_mark: 	| 

                 	

[1]: For enterprise version only

[2]: In a paid tier


## How will we make money?
From a sustainability point of view, for us and for this open source project, it's important that we make profit. So far, we plan to charge for:
- Hosting of the SuperTokens service. This can be done in a way that uses our database instances, or yours.
- A pro version that has (this may be charged on a per user basis):
    - Multi region & sharding support for scaled apps
    - A dashboard for session and user management
    - Feature for compliance requirements 
    - Advanced threat detection features
    - Feature roadmap is coming soon...
- A commercial license that dictates:
    - Different levels of support
    - Liability agreement
    - Building custom features
- Monthly sponsorship

### Backers
<a href="https://www.ycombinator.com/"><img width="75" src="https://www.ycombinator.com/assets/ycdc/ycombinator-logo-7481412385fe6d0f7d4a3339d90fe12309432ca41983e8d350b232301d5d8684.png"></a>


## Why Java?
- Java has a very mature ecosystem. This implies that third party libraries have been battled tested since a very
 long time. This adds an additional security benefit.
- Java's strong type system ensures fewer bugs and easier maintainability. This is especially important when
 many people are expected to work on the same project.
- Ability to dynamically load JARs allows us to distribute only the right database plugin, minimising the final
 Docker image size.

## Building from source
Instructions coming soon...

## Community
- [Discord](https://supertokens.io/discord)
- [Email](mailto:team@supertokens.io)

If you think this is a project you could use in the futrue, please :star2: this repository!

### Contributors
<table>
  <tr>
    <td align="center"><a href="https://github.com/rishabhpoddar"><img src="https://avatars1.githubusercontent.com/u/2976287?s=460&u=d0cf2463df96fbdf1138cf74f88d7cf41415b238&v=4" width="100px;" alt=""/><br /><sub><b>Rishabh Poddar</b></sub></a></td>
    <td align="center"><a href="https://twitter.com/Advait_Ruia"><img src="https://pbs.twimg.com/profile_images/1261970454685900800/ALVzsBQJ_400x400.jpg" width="100px;" alt=""/><br /><sub><b>Advait Ruia</b></sub></a></td>
    <td align="center"><a href="https://github.com/bhumilsarvaiya"><img src="https://avatars2.githubusercontent.com/u/21988812?s=460&u=c0bcde60a8bf1a99baafced55dd1a8d901fa7e4a&v=4" width="100px;" alt=""/><br /><sub><b>Bhumil Sarvaiya</b></sub></a></td>
    <td align="center"><a href="https://github.com/jscyo"><img src="https://i.stack.imgur.com/frlIf.png" width="100px;" alt=""/><br /><sub><b>Joel Coutinho</b></sub></a></td> 
  </tr>
  <tr>
   <td align="center"><a href="https://github.com/RakeshUP"><img src="https://avatars1.githubusercontent.com/u/20946466?s=400&u=01d7d6d701eedd8345e491172e3af04578d18113&v=4" width="100px;" alt=""/><br /><sub><b>Rakesh UP</b></sub></a></td>
   <td align="center"><a href="https://twitter.com/mufassirkazi"><img src="https://i.stack.imgur.com/frlIf.png" width="100px;" alt=""/><br /><sub><b>Mufassir Kazi</b></sub></a></td>
<td align="center"><a href="https://github.com/nkshah2"><img src="https://avatars2.githubusercontent.com/u/18233774?s=400&u=5befa41674cfcd6c6060103360ab323cdfa24dcb&v=4" width="100px;" alt=""/><br /><sub><b>Nemi Shah</b></sub></a></td>
<td align="center"><a href="https://github.com/irohitb"><img src="https://avatars3.githubusercontent.com/u/32276134?s=400&u=0b72f6c4e6cfa749229a8e69ed86acb720a384e7&v=4" width="100px;" alt=""/><br /><sub><b>Rohit Bhatia</b></sub></a></td>
  </tr>
</table>

## Contributing
Instructions coming soon

## Development history
Over the last few months, we have built out session management for SuperTokens. During this period, we have made our
 fair share of mistakes:
 - Our first version was architected such that it tightly coupled the backend and database layer. So we had one
  `npm` library for NodeJS with MySQL, and another one for NodeJS with MongoDB etc. When adding support for a new
   backend framework, majority of the logic and tests needed to be rewritten. It became clear that we needed to add a
    service in the middle. We do realise that adding this service means it's harder to get started and that there is
     an extra point of failure, however from the perspective of supporting each tech stack, this decision makes sense, since the failure problem can be addressed through easy to implement technical means.
 
- Until August, 2020, our license was not truly open source. This was done as an experiment to get feedback on the
  importance of software license for the startup community. Since then, it's become very clear that we must use a
   standard open source license, so we chose Apache 2.0
   
- Our community version used to ping our APIs from time to time. This was done for us to understand
 adoption of our session management solution. However, it quickly became clear that that was a bad move.
 
- We used to have a notion of a license key that was required to use the community version. This license key was
 issued by us, and would never expire. Some parts of the code still refer to that, however, it's only for backwards
  compatibility. For all intents and purposes, a license key doesn't exist for any new user.

## License
Copyright (c) SuperTokens, Inc. All rights reserved.

Licensed under the Apache 2.0 license.
