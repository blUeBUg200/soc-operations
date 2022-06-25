# Security Operation Centre Functional Model (SFM)

SOC Functional Model (SFM) helps organizations to plan & prepare setting up an new SOC or to asses your exisitng SOC capabilities and identify the areas to focus.

Requesting the audience to have basic understanding of below topics before jumping into the described process for better understanding,

| [Neo4j](https://neo4j.com/)        | [MaGMa UCF](https://www.betaalvereniging.nl/en/safety/magma/)           | [MITRE ATT&CK](https://attack.mitre.org/)  | [SOC Assessment](https://mad-certified.mitre-engenuity.org/group/283477)        | [MITRE Navigator](https://mitre-attack.github.io/attack-navigator/)           | [Threat Modeling](https://redcanary.com/blog/threat-modeling/)  | [Threat Intelligence](https://mad-certified.mitre-engenuity.org/group/283476)        | [Threat Emulation](https://mad-certified.mitre-engenuity.org/group/359563)           | [DeTT&CT Framework](https://github.com/rabobank-cdc/DeTTECT)  | [Crown Jewel Analysis](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/crown-jewels-analysis) | [Risk Remediation Analysis](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/cyber-risk-remediation-analysis)

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
 
### Age:I.M2 - Log Quality Analysis
Integrate the assets with centralized management solution such as Security Information & Event Management(SIEM). Post integration, the logs should be subjected to below checks to ensure it adds value to our security monitoring,

- Device Completeness
- Data Field Completeness
- Timeliness
- Consistency
- Retention

more details on the above topics can be found [here](https://github.com/blUeBUg200/bluenightingale#pick-a-mitre-data-source) 

### Age:I.M3 - Primary Analytics
In this stage we will build our first set of usecases to detect anomalies around our crown jewel assets. Below are the few categories of usecases (feel free to add more based on your environment)

- Internet to Intranet (and vice-versa) connection on suspicious ports such as 445, 3389, 22, etc.,
- VPN connections from non-business countries
- Brute Force Login Attempts
- Phishing email
- Intranet Port Scanning

> Age:I.M3 might produce high False Positive alerts if we haven't understood the environment better (both N-->S and E-->W traffic behavior to be gathered and excluded as part of known behaviors)

## Age II
This stage is more of an intelligence driven approach to detect, alert and degrade attackers actions against an environment.

<img width="914" alt="Age II" src="https://user-images.githubusercontent.com/86832373/175767639-97a5d5e5-24fb-49ec-8f85-52265bf2b576.png">

### Age:II.M1 - Threat Modeling
In this stage we will gather the list of adversaries who might be interested against your crown jewel assets. The adversaries might land in your environment based on below factors,

- Industry
- Available Technology
- Geographical Location

The output of this stage will produce adversary list from whom we will defend our network. 

> Say for example out out has given APT29 and APT 30 as our adversary.

For more details on threat modeling refer [Threat Modeling](https://redcanary.com/blog/threat-modeling/)

### Age:II.M2 - Intelligence driven Analytics
From the previous stage (Age:II.M1) output we have compiled a TTP map for the adversaries,
- APT 29 [Matrix](https://github.com/blUeBUg200/soc-operations/blob/main/APT29.svg)
- APT 30 [Matrix](https://github.com/blUeBUg200/soc-operations/blob/main/APT30.svg)

The combination of TTP by both threat groups is compiled with the help of MITRE Navigator and the output will look something like [this](https://github.com/blUeBUg200/soc-operations/blob/main/APT_Combined.svg)

No we have list of TTPs for which we need to create detection usecases.

There are plenty of resources which will help building the usecase repositiory. Listing few sites for reference,

- [Redcanary](https://redcanary.com/threat-detection-report/threats/)
- [Sigma](https://github.com/SigmaHQ/sigma/tree/master/rules)

### Age:II.M3 - Risk Remediation Analysis**

During this stage we will analyze the list of security controls which will be helpful in defending against the adversary TTPs(in our case APT29 and APT30). Upon research, I found MITRE Engenuity [security-stack-mapping](https://github.com/center-for-threat-informed-defense/security-stack-mappings) for Azure and AWS. However, this is still a research topic for me wherein I am looking for something more similar to Engenuity project for on-premise IT environment. If you know any references, kindly share your inputs through [email](kaviarasan1195@gmail.com)

## Age III

<img width="914" alt="Age III" src="https://user-images.githubusercontent.com/86832373/175775321-e570f00a-7aff-437a-a3b1-9a46be5b9c0c.png">

## Age IV

<img width="914" alt="Age IV" src="https://user-images.githubusercontent.com/86832373/175775420-576c37af-581a-498f-bdc6-29657ed21950.png">

## SOC Iteration Model

<img width="914" alt="Iteration Model" src="https://user-images.githubusercontent.com/86832373/175775983-f9b6ee18-02db-44a7-b22a-44fd7b65410a.png">

SFM model was designed based on my understanding of SOC and the requirements it should full-fill to combat cyber threats. Feel free to reach me through email (kaviarasan1195@gmail.com) for queries and feedback.
