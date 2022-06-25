# Security Operation Centre Functional Model (SFM)

SOC Functional Model (SFM) helps an organization to plan & prepare setting up an new SOC or to asses your exisitng SOC capabilities and identify the areas to focus.

Requesting the audience to have basic understanding of below topics before jumping into the described process for better understanding,

[Neo4j](https://neo4j.com/)

[MaGMa UCF](https://www.betaalvereniging.nl/en/safety/magma/)

[MITRE ATT&CK](https://attack.mitre.org/)

[SOC Assessment](https://mad-certified.mitre-engenuity.org/group/283477)

[MITRE Navigator](https://mitre-attack.github.io/attack-navigator/)

[Threat Modeling](https://redcanary.com/blog/threat-modeling/)

[Threat Intelligence](https://mad-certified.mitre-engenuity.org/group/283476)

[Threat Emulation](https://mad-certified.mitre-engenuity.org/group/359563)

[DeTT&CT Framework](https://github.com/rabobank-cdc/DeTTECT)

[Crown Jewel Analysis](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/crown-jewels-analysis)

[Risk Remediation Analysis](https://www.mitre.org/publications/systems-engineering-guide/enterprise-engineering/systems-engineering-for-mission-assurance/cyber-risk-remediation-analysis)


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
- Prepare for Threat Profiling
    - Plan for resources and references for creating a threat profile
 
### Age:I.M2 - Log Quality Analysis
The integrated device logs should be analyzed on the below perspectives to ensure it adds value to our security monitoring,

- Device Completeness
- Data Field Completeness
- Timeliness
- Consistency
- Retention

more details on the above topics can be found [here](https://github.com/blUeBUg200/bluenightingale#pick-a-mitre-data-source) 

### Age:I.M3 - Primary Analytics
In this stage we will build our first set of usecases to detect anomalies around our crown jewel assets. The usecases might include but not restricted to below,

- Internet to Intranet (and vice-versa) connection on suspicious ports such as 445, 3389, 22, etc.,
- VPN connections from non-business countries
- Brute Force Login Attempts
- SPAM email
- Intranet Port Scanning

> Age:I.M3 might produce high False Positive alerts if we forget to understand the environment better (both N-->S and E-->W traffic behavior to be gathered and excluded as part of known behaviors)

## Age II

SFM model was designed based on my understanding of SOC and the requirements it should full-fill to combat cyber threats. Feel free to reach me through email (kaviarasan1195@gmail.com) for queries and feedback.
