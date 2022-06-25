# Security Operation Centre Functional Model (SFM)

SOC Functional Model (SFM) helps organizations to plan & prepare setting up an new SOC or to asses your exisitng SOC capabilities and identify the areas to focus.

Requesting the audience to have basic understanding of below topics before jumping into the described process for better understanding,

- [MITRE ATT&CK](https://attack.mitre.org/)  | [SOC Assessment](https://mad-certified.mitre-engenuity.org/group/283477)        | [MITRE Navigator](https://mitre-attack.github.io/attack-navigator/)           | [Threat Modeling](https://redcanary.com/blog/threat-modeling/)  

- [Threat Emulation](https://mad-certified.mitre-engenuity.org/group/359563)           | [DeTT&CT Framework](https://github.com/rabobank-cdc/DeTTECT)  | [MITRE CJA](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/crown-jewels-analysis) | [Risk Remediation Analysis](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/cyber-risk-remediation-analysis)

# The SFM Model

SFM consists of 5 stages to build a new SOC and 4 stages to asses your exisiting SOC.


<img width="914" alt="SFM Stages" src="https://user-images.githubusercontent.com/86832373/175633961-917f4da8-5f33-431e-833c-a76ebf31a1de.png">


## Infancy
This stage applies only for organizations who are planning to setup Security Operation Centre (SOC) for first time. Below aspects can be decided during the process of planning

<img width="914" alt="Infancy" src="https://user-images.githubusercontent.com/86832373/175763326-1c7d0d1c-6e8e-46d9-9306-ce78d68e1e5e.png">


### Infancy.M1 - Monitoring Scope
SOC monitoring scope (such as only production, production + development, production + development + disaster recovery) based on business requirement

### Infancy.M2 - Tools Procurement
Procurement of SOC tools with high Return of Investment (such as Security Information & Event Management, Endpoint Detection & Response, Network Detection  & Response)

### Infancy.M3 - Mode of Operation
Mode of SOC operation to be decided such as In-House or Managed Security Service Provider(MssP)

## Age I
This stage is about understanding the environment, business and assets which are of high value target for an attacker.

<img width="914" alt="Age I" src="https://user-images.githubusercontent.com/86832373/175763566-0cce41b9-cbe1-44fa-9dc9-4bcb6101a8f9.png">

### Age:I.M1 - Crown Jewel Analysis
- Understand Mission Priorities
    - Understand the business focus and its missions
    - Identify relevant assets which drive the mission's success
- Identify Mission Dependencies
    - Identify dependencies for the mission critical assets

> Topic Reference(s): 
> [MITRE CJA](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/crown-jewels-analysis)

> **_NOTE:_** Planning to build a asset dependency graph with the help of [Neo4j](https://neo4j.com/). If you know any references or exisiting FOSS projects which has this module inbuilt, kindly shoot an email to kaviarasan1195@gmail.com with the references attached.

### Age:I.M2 - Log Quality Analysis
Integrate the assets with centralized management solution such as Security Information & Event Management(SIEM). Post integration, the logs should be subjected to below checks to ensure it adds value to our security monitoring,

- Device Completeness
- Data Field Completeness
- Timeliness
- Consistency
- Retention

> Topic Reference(s):  [Log Quality Check](https://github.com/blUeBUg200/bluenightingale#pick-a-mitre-data-source)

### Age:I.M3 - Primary Analytics
In this stage we will build our first set of usecases to detect anomalies around our crown jewel assets. Below are the few categories of usecases (feel free to add more based on your environment)

- Internet to Intranet (and vice-versa) connection on suspicious ports such as 445, 3389, 22, etc.,
- VPN connections from non-business countries
- Brute Force Login Attempts
- Phishing email
- Intranet Port Scanning

> **_NOTE:_** Age:I.M3 might produce high False Positive alerts if we haven't understood the environment better (both N-->S and E-->W traffic behavior to be gathered and excluded as part of known behaviors)

## Age II
This stage is more of an intelligence driven approach to detect, alert and degrade attackers actions against an environment.

<img width="914" alt="Age II" src="https://user-images.githubusercontent.com/86832373/175767639-97a5d5e5-24fb-49ec-8f85-52265bf2b576.png">

### Age:II.M1 - Threat Modeling
In this stage we will gather the list of adversaries who might be interested against your crown jewel assets. The adversaries might land in your environment based on below factors,

- Industry
- Available Technology
- Geographical Location

The output of this stage will produce adversary list from whom we will defend our network. 

> **_NOTE:_** Say for example, our output from previous step has given APT29 and APT 30 as our adversary and going forward this adversary profile is called "Threat Book"

> Topic Reference(s): [Threat Modeling](https://redcanary.com/blog/threat-modeling/)  

### Age:II.M2 - Intelligence driven Analytics
From the previous stage (Age:II.M1) output we have compiled a TTP map for the adversaries,
- APT 29 [Matrix](https://github.com/blUeBUg200/soc-operations/blob/main/APT29.svg)
- APT 30 [Matrix](https://github.com/blUeBUg200/soc-operations/blob/main/APT30.svg)

The combination of TTP by both threat groups is compiled with the help of MITRE Navigator and the output will look something like [this](https://github.com/blUeBUg200/soc-operations/blob/main/APT_Combined.svg). Now we have list of TTPs for which we need to create detection usecases.There are plenty of resources which will help building the usecase repositiory. Listing few sites for reference,

- [Redcanary](https://redcanary.com/threat-detection-report/threats/)
- [Sigma](https://github.com/SigmaHQ/sigma/tree/master/rules)

> **_NOTE:_** IOC based intelligence to detect our "Threat Book" should be collected with the help of Threat Intelligence Platform such as MISP.

### Age:II.M3 - Risk Remediation Analysis

During this stage we will analyze the list of security controls which will be helpful in defending against the adversary TTPs(in our case APT29 and APT30). This is a hands-on excercise to understand the detection, deny, degarde and deceive capabilities of the security tools and map them to MITRE matrix against our "Threat Book" TTPs.

> **_Research Topic:_** Upon research, I found MITRE Engenuity [security-stack-mapping](https://github.com/center-for-threat-informed-defense/security-stack-mappings) for Azure and AWS.This is still a research topic for me wherein I am looking for something more similar to Engenuity project for on-premise IT environment. If you know any references or exisiting FOSS projects which has this module inbuilt, kindly shoot an email to kaviarasan1195@gmail.com with the references attached.

> Topic Reference(s): [Risk Remediation Analysis](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/cyber-risk-remediation-analysis; [SOC Assessment](https://mad-certified.mitre-engenuity.org/group/283477) 

## Age III
During this stage, more proactive actions are conducted which helps SOC to respond faster to cyber threats.

<img width="914" alt="Age III" src="https://user-images.githubusercontent.com/86832373/175775321-e570f00a-7aff-437a-a3b1-9a46be5b9c0c.png">

### Age:III.M1 - MITRE Detection Coverage
Based on the stage (Age:II.M1) we know the list of TTP to detect and from stages (Age:II.M2) & (Age:II.M3) we can compile a matrix which portrays the list of TTP we can detect, alert, deceive and degrade the attackers progress.

Create a MITRE Att&ck layer combining all the three and have a clear understanding of the below,
- Techniques we can detect
- Techniques we can degrade and deceive
- Techniques we can deny

Based on the above we might endup with few TTPs remained untouched by all categories (deny, detect, deceive or degarde). A detailed research should be conducted against the list and threat-informed decisions need to be made (either enable logging or purchase of new security controls)

> Topic Reference(s): [MITRE Navigator](https://mitre-attack.github.io/attack-navigator/)

### Age:III.M2 - Security Automation
Automations to reduce man efforts on repeated tasks should be incorporated.

### Age:III.M3 - Vulnerability Management
Vulnerability Assessment gives more visibility about the assets driving with high critical vulnerabilities. Periodic patch management and vulnerability assessment hand by hand provides more visibility to the security posture of the organization.

### Age:III.M4 - Threat Hunting
The process of threat hunting is briefed in one of writings earlier. Follow this [link](https://github.com/blUeBUg200/bluenightingale#soc---the-blue-nightingale) for more details.

## Age IV

<img width="914" alt="Age IV" src="https://user-images.githubusercontent.com/86832373/175775420-576c37af-581a-498f-bdc6-29657ed21950.png">

### Age:IV.M3 - Threat Emulation
Threat Emulation will help organization to understand their capability to detect when an threat profiled adversary in conductiong their operation against the environment. The mimicked Techniques need to be emulated and the security usecase alerting efficiency need to be validated post emulation activity.

## SOC Iteration Model

As mentioned in the introuduction, the stages are iterative process and keeps changing as the organization mission changes, priority changes. 
Below picture shows the repeat loop of the stages which will be iterated over a period of time.

<img width="1085" alt="Iteration Model" src="https://user-images.githubusercontent.com/86832373/175778782-0021521f-9224-4a80-b75f-77cce7f68b1d.png">

- Repeat Q : Operates when your emulation excercise output shows proven detection gaps which need to be fixed.
- Repeat W : Operates when you business mission changes, priority changes and the environment expands.

SFM model was designed based on my understanding of SOC and the requirements it should full-fill to combat cyber threats. Feel free to reach me through email (kaviarasan1195@gmail.com) for queries and feedback.
