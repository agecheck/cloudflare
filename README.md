# Using Cloudflare with Agegate

This repository contains configuration examples and a sample Cloudflare Worker for injecting an X-Age-Gate header to enable geo-targeted age enforcement. The included settings are compatible with Cloudflare’s free tier.

## Age-Verification Laws Covered

| Jurisdiction        | Law / Authority                              |
|--------------------|-----------------------------------------------|
| European Union     | Digital Services Act (DSA)                    |
| United Kingdom     | Online Safety Act 2023                        |
| France             | ARCOM enforcement framework                   |
| United States      | State age-verification laws (varies by state) |
| Australia          | Online Safety Act 2021                        |

---

## Country based header injection

1. On Cloudflare dashboard, make a new Response Header Transform Rule
2. Name the rule **Country Based Age Gate Heading**

   When incoming requests match…

   select wildcard unless you want only specific sections of your website to have the age-gate

3. write the rule.  See below for standard patterns based on the content of your website and current laws
~~~
ip.src.country in {"FR" "GB"}
~~~

4.  Then...

   Add a static response header of X-Age-Gate =  true

5.  Place at First Order


## Region based header injection (U.S. state-by-state law compliance)

Cloudflare does not allow injecting a rules based header on its free plan based on region. Therefore, to inject a header for U.S. states, first add a rule that US based traffic must pass to a worker, and then use the worker in this repo to inject an age gate header based on the state.



## Settings based on type of website content

### Adult Content

As of February 2026, the following countries require age verificaton for adult content:  
source: 

Therefore, the following setting is suggested:

~~~
ip.src.country in {"FR" "GB"}
~~~

#### Adult Content – Age-Verification Laws

| Jurisdiction              | Law / Authority                                  | Minimum Age |
|--------------------------|---------------------------------------------------|-------------|
| European Union           | Digital Services Act (DSA)                        | 18+         |
| United Kingdom           | Online Safety Act 2023                            | 18+         |
| France                   | ARCOM enforcement framework (Audio-visual Code)   | 18+         |
| United States – Texas    | HB 1181                                           | 18+         |
| United States – Louisiana| Act 440                                           | 18+         |
| United States – Utah     | SB 287                                            | 18+         |
| United States – Arkansas | Act 612                                           | 18+         |
| United States – Mississippi | HB 1315                                      | 18+         |
| Australia                | Online Safety Act 2021                            | 18+         |
---

### Social Media Content

As of February 2026, the following countries require age verificaton for social media:  

Therefore, the following setting is suggested:

~~~
ip.src.country in {"FR" "GB"}
~~~

### Gambling Content

As of February 2026, the following countries require age verificaton for websites with gambling:  

Therefore, the following setting is suggested:

~~~
ip.src.country in {"FR" "GB"}
~~~

### Tobacco Content

As of February 2026, the following countries require age verificaton for websites with tobacco promotion content:  

Therefore, the following setting is suggested:

~~~
ip.src.country in {"FR" "GB"}
~~~

### Alcohol Content

As of February 2026, the following countries require age verificaton for websites with alcohol promotion content:  

Therefore, the following setting is suggested:

~~~
ip.src.country in {"FR" "GB"}
~~~

---

# Important Disclaimer

This repository and README do not constitute legal advice. No warranty or representation is made regarding the accuracy or completeness of the regulatory references provided. No warranty or representation is made regarding Cloudflare’s services or the accuracy of its IP geolocation. Cloudflare is a registered trademark of Cloudflare, Inc. Cloudflare has not endorsed or reviewed the contents of this repository.




