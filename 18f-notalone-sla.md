# 18F Service Level Agreement (SLA)

## 18F Background

18F is a digital services delivery team located within the General Services Administration (GSA). We are a team of public servants who work as developers, designers, and change catalysts. Our mission (and strategy) is to deliver great software and services at low cost to our Federal partners using modern methodologies, especially human centered design and agile development.

## NotAlone Background

NotAlone is a static site, with a search capability, to help the public find Information for students, schools, and anyone interested in resources on how to respond to and prevent sexual assault on at schools, colleges, and universities.

### Scope

“NotAlone” means major releases of the software (e.g., 1.x, 2.x) in its final production architecture. This agreement does not include releases before a 1.0, or in a non-production architecture (dev, test, QA, performance testing, etc). 18F will strive to meet all SLA requirements for all releases, but these cannot be guaranteed. 

## Data ownership

Data and source code for the NotAlone system, and all of its dependencies, can be exported and transferred at any time, at no cost to you.

## Operational and finance model

This partnership is governed by an interagency agreement (IAA) between the GSA and the Department of Education. Under this IAA, we charge only our actual costs: primarily our time, our infrastructure, our platforms, and a small amount of overhead for our general team operations. We do not make a profit and are expressly prohibited from doing so. We don't charge any overhead or fees for the use of our infrastructure; whatever we pay our vendors is what you pay.

### An open source team

We place a premium on developing digital tools and services in the open. Doing so improves the final product we create. Our [open source policy](https://github.com/18F/open-source-policy/blob/master/policy.md) was developed after consulting previous work done by the Department of Defense (DoD), the Consumer Financial Protection Bureau (CFPB), and the Office of Management and Budget (OMB). By default, we:

* use Free and Open Source Software (FOSS) in our projects and to contribute back to the open source community;
* create an environment where _any_ project can be developed in the open; and
* publish all source code created or modified by 18F publicly.

A FOSS project provides critical technical benefits like unrestrained product customization and interoperability between tools. See [our policy](https://github.com/18F/open-source-policy/blob/master/policy.md#benefits) for more about the benefits of this approach.

## Infrastructure as a Service (as a Service)

18F uses industry standard IaaS solutions to deliver software as a service (SaaS) to our partners. Under this model, 18F abstracts complexity away from you. 

We manage:

* _Infrastructure_: We currently offer only one IaaS solution, Amazon Web Services (AWS), in their *US-East/US-West* (E/W) regions and in the AWS *GovCloud*. We operate our IaaS under a _DevOps_ model: While we do have a fundamental "separation of concerns" between our developers and our operations staff (engineering, architecture, and cybersecurity), under DevOps, these teams work closely together to deliver working software. Everyone is responsible for every step in the process to deliver software into production. 

* _Procurement_: We maintain blanket purchase agreements (BPAs) and issue task orders for specific clients if additional infrastructure capacity is needed on the procurement vehicle. We have Federal staff available to help you create an independent government cost estimate (IGCE) for your future costs.

* _Cybersecurity compliance_: We only use [FedRAMP IaaS](http://cloud.cio.gov/fedramp/cloud-systems) at 18F. The FedRAMP program is run by our colleagues at GSA, with additional partners at the DoD, DHS, and NIST. FedRAMP is an extension of the controls recommended by the NIST 800-53 guidance. It's specifically targeted at "cloud solutions" like IaaS. Both AWS E/W and the AWS GovCloud are physically located in the continental United States and have active FedRAMP authorizations. 

* _Privacy compliance_: We conduct our own privacy impact assessments (PIAs) and file system of records notices (SORNs) where appropriate.


* _Paperwork Reduction Act (PRA)_: We conduct our own PRAs and have a close working relationship with OIRA/OMB.


18F strongly recommends the use of the AWS E/W for all net-new system development, unless you require compliance with [International Traffic in Arms Regulations (ITAR)](https://www.pmddtc.state.gov/regulations_laws/itar.html). There are multiple value-added components within AWS E/W that are unavailable in the AWS GovCloud; many of these directly help with the auditability and security of the system. AWS E/W services are also available at a lower rate than those in the AWS GovCloud.

_If you deploy your own applications on our IaaS, you are responsible for the compliance, performance, and operation of your systems._

### Response Time and Capacity Management

Ninetieth (90th) percentile response time of a webpage request should be within 7 seconds. In cases where there is a temporary or permanent surge in traffic that is resulting in slower response times, we will ensure that NotAlone’s infrastructure is scaled appropriately to speed up response times.

If a significant promotional campaign or media coverage is planned, the NotAlone Product Owner should communicate to the 18F Product Lead in advance of such planned or known events to ensure the highest levels of availability and performance, The lead time for such notices can be as short as 48 hours.

### Uptime

18F inherits the uptime numbers in the AWS Service Level Agreement (SLA). You can find the SLA of some of the most common AWS components online:

* [EC2](http://aws.amazon.com/ec2/sla/)
* [S3](http://aws.amazon.com/s3/sla/)
* [RDS](http://aws.amazon.com/rds/sla/)

At the application level, 18F strives for 99% uptime. Any outage at the application level will trigger an automated alert to our support team who will act to restore the service to full operation (e.g., workaround) immediately. 18F will notify the NotAlone Product Owner of the outage within 2 hours along with an explanation of the outage and steps to remediate the underlying cause(s) within seven (7) business days.

### IaaS Failover

NotAlone is currently set up in the AWS GovCloud region. If the AWS GovCloud goes down for more than one (1) hour, 18F will re-build NotAlone in one of the AWS East regions within four (4) hours. 18F intends to move NotAlone to the AWS Global S3 architecture and enable the AWS CloudFront content delivery network (CDN) for increased reliability and resiliency. 

## DevOps

For software that we develop, procure, or operate at 18F, our DevOps team will provide _continuous_:

* _configuration management_ - we use tools such as Chef and Cloudformation to represent our infrastructure as code (IaC). Ensuring your entire system as IaC ensures a high degree of repeatability, auditability, and security. Just like all of our code, we check our IaC into a distributed version control system (DVCS) using git.

* _monitoring_ - we use tools such as Cloudtrail, Splunk and NewRelic

* _integration and deployment_ - we use tools such as Capistrano and Jenkins

* _incident response_ - if there is an incident on your systems, we will contact the NotAlone Product Owner per the [Federal incident notification guidelines](https://www.us-cert.gov/government-users/reporting-requirements#tax). 

We work closely with and monitor alerts from US-CERT and the open source community more broadly.

### Concept of Operations

The 18F DevOps team manages the AWS infrastructure, in direct collaboration and consultation with our senior application developers and the GSA Security Engineering team. The root user is Noah Kunin, 18F's Delivery Architect (noah.kunin@gsa.gov). Administrative users (with almost all the powers of the root user) are limited to users trained on AWS. All users, regardless of their permission levels, must sign into the platform using a password in excess of NIST guidelines and using 2-factor authentication (2FA).

Firewalls and overall data flow through the system are maintained by the usage of security groups. Each resource in AWS is limited by a pure whitelist - an 18F administrator must specifically enumerate ports. Each system developed by 18F receives its own internet gateway and virtual private cloud (VPC) to logically separate it from other systems in the environment. Identity access management is mediated through permission policies written in JSON. SSH Key-pairs are then assigned to appropriate users. Key-pairs are only ever stored in a GSA enclave or locally on staff laptops. The security group policy on the VPC or specific instance then limits SSH access to a GSA CIDR block, or other known and trusted entities based on system design or functionality.

18F works hard to ensure every component of our applications, and as much of our IaaS as possible, is based on free and open source (FOSS) technologies. We always evaluate open source solutions first. If you choose not to use 18F's IaaS in the future, the vast majority of the system should be transferrable without any need to purchase licenses or negotiate intellectual property rights. 18F can provide you a comprehensive system architecture diagram before your system moves into production, noting where non-open source components are used.

### Shared responsibility 

In cases where you have engineers, developers, or other users who wish to share the responsibility of the system with 18F, we are able to provision your users if they meet the above standards. Depending on the nature of the responsibility, your users would have "administrative-like" permissions but only to VPCs that pertain to your systems. These users must go through the same training as 18F staff, regardless of their expertise with AWS or any other infrastructure. Experience with Linux (preferably Debian/Ubuntu, but RedHat Enterprise Linux or CentOS is acceptable) is also required for access.

## Technical service notes

Ancillary to our application development and DevOps are other services your system may need when deployed to production.

### Domain Name Service (DNS)

18F leverages AWS' solution, Route53, to load balance your application and provide availability, disaster recovery, and overall system flexibility. DNS services are only available if 18F is hosting your system. 

If you require a:

* second-level domain (example.gov): 18F will work with the Federal CIO, OMB, and the DotGov.gov team (located at GSA) on your behalf to get the necessary permissions to launch.


* third-level domain (example.youragencyhere.gov): 18F will work with your Network team to establish a CNAME record (an alias) from the desired URL to the 18F AWS infrastructure. This is usually achieved by your Network team adding a CNAME record for the URL to the fully qualified domain name (FQDN) of the primary Elastic Load Balancer (ELB) on your system. You can also fully delegate control over the third-level domain over to 18F. For staging, we recommend hyphenated third-level domains (e.g., example-staging.youragency.gov) to make SSL for staging environments a simpler process.


* fourth-level domains and above: 18F does not recommend the use of publicly accessible domains beyond the third-level. They are difficult to type for users and difficult to use in marketing and communications. If you think you have a discrete need for a fourth-level or higher domain, please contact 18F as soon as possible, so we can first look at re-architecting your system. Fourth-level and higher domains are appropriate for non-production environments (ex: development.example.youragencyhere.gov)


DNSSEC capabilities are not currently available using this service. As none of the major web browsers currently support DNSSEC validation capabilities, true DNSSEC compliance is not yet achievable, regardless of your DNS provider. 

(If you are already using a content delivery network (CDN) like Akamai, you are already out of compliance with DNSSEC, since no Federal CDN vendor has yet to solve the problem of dynamically changing zone files with millions of entries every few seconds.)

18F is committed to working with the community on DNSSEC and DNS security in general. We will closely monitor browser DNSSEC capabilities along with other clients and actively explore compensating controls.

In the meantime, if you are connecting into 18F’s backend systems to exchange sensitive data, we ensure you are working with the correct IP address before activating an exchange. If you are connecting into 18F’s front-end systems (like an API) to exchange sensitive data, we will use the appropriate authentication mechanism (e.g., API keys, SSL/TLS encryption, OAuth) to protect your data.

### IPv6

While 18F and GSA fully concurs with the move to IPv6, currently AWS does not support IPv6 in VPCs. The operational performance and security gains achieved by this best practice architecture outweigh the IPv6 compliance need.

The main purpose of the IPv6 policy is to ensure Federal operations are not disrupted by an eventual exhaustion of IPv4 addresses. AWS has been very proactive in obtaining IPv4 blocks for its customers and we do not anticipate any disruption of operations. 

One strategy that 18F uses to mitigate the risks of IPv4 address exhaustion is through the use of Elastic Load Balancers (ELBs). Each ELB is a single IP that sits atop a pool of private instances - the ELB itself is an abstraction that does not provide a "true" IPv4 address, but instead is a FQDN that dynamically represents the pool of private instances. 18F always pre-reserves an address for its ELBs, so long before we enter production, we know if there will be an issue.

At the same time, many of our Federal partners (including GSA) do not have IPv6 compatible network systems, making it impossible to successfully test IPv6 functionality within the networks we operate. So even if IPv6 capabilities were deployed tomorrow, we would be reticent to make commitments to a feature we ourselves cannot test.

AWS is planning on deploying IPv6 capabilities to VPCs in the future and long before the IPv4 exhaustion impacts AWS customers such as 18F. We hope GSA and our partners have fully enabled internal and external IPv6 networks by that point.

## NotAlone Compliance Architecture

We have prepared the following breakdown of various compliance checks:


-  Section 508: NotAlone was assessed for 508 compliance by our in-house, trained and certified evaluator. All identified issues were resolved.

- PRA: No OMB control # is required as the NotAlone site does not collect any information via methods that fall under the PRA.

- SORN: No SORN is required as no information that falls under the Privacy Act is collected. 

Overall analytics data is collected via the GSA-run Government Enterprise Google Analytics account as long as the system is in operation. 

- ATO: After leveraging the AWS FedRAMP authorization, we implemented the following controls for NotAlone to ensure confidentiality, integrity, and availability of the system at the FISMA Low level. 

- AC-2 Account Management
- AU-2 Audit Events
- AU-6 Audit Review, Analysis, and Reporting
- CM-3 Configuration Change Control
- CM-6 Configuration Settings
- IA-2 Identification and Authentication (Organizational Users)
- IA-2 (1) Identification and Authentication (Organizational Users) | Network Access to Privileged Accounts
- IA-2 (2) Identification and Authentication (Organizational Users) | Network Access to Non-Privileged Accounts
- PL-8 Information Security Architecture
- SI-2 Flaw Remediation
- SI-10 Information Input Validation
- CA-8 Penetration Testing RA-5 Vulnerability Scanning
- SA-11 (1) Developer Security Testing and Evaluation | Static Code Analysis
- CM-2 Baseline Configuration
- SC-7 Boundary Protection
- CM-8 Information System Component Inventory

18F also performed: 

  * risk analysis, including the creation of a system security plan
  * vulnerability scanning (e.g., Nessus, Tripwire)
  * static code analysis (e.g., HP Fortify, Checkmarx, Hariki)
  * penetration testing

18F is the System Owner of NotAlone. ("System Owner" is a term of art, defined in [NIST Special Publication 800-18, 
Revision 1, Guide for Developing Security Plans for Federal Information Systems](http://csrc.nist.gov/publications/nistpubs/800-18-Rev1/sp800-18-Rev1-final.pdf).) The 18F/GSA Authorizing Official signed an ATO to put NotAlone into production under the current controls for no more than (1) one year under its current set of functions. 18F will renew or replace this ATO before it expires.

#### Design and code bug fixes

18F identifies bugs from a variety of sources.

Per the governing IAA, the NotAlone Product Owner determines the priority of all product backlog items, including bugs. The 18F delivery team will work to implement and deploy those items in a manner that is commensurate with the priority and available resources.

All product backlog items, including bugs, are recorded in the [NotAlone Github repo](https://github.com/18F/NotAlone/issues). Each issue logged is labeled according to priority, workflow status, etc. Those with the highest level priorities will be implemented and deployed first.

#### Contact information

**General inquiries:** 18F@gsa.gov

**DevOps:** devops@gsa.gov

**Interagency Agreements:** Aaron Snow -  aaron.snow@gsa.gov

**NotAlone Project Lead:** TBD

**NotAlone Technical Lead:** Aaron Snow - aaron.snow@gsa.gov

