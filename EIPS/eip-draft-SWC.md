---
eip: <to be assigned>
title: Smart Contract Weakness Classification (SWC)
author:  Gerhard Wagner (@thec00n)
discussions-to: https://ethereum-magicians.org/XXX
status: Draft
type: Informational
created: 2018-09-18
---

<!--You can leave these HTML comments in your merged EIP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. This is the suggested template for new EIPs. Note that an EIP number will be assigned by an editor. When opening a pull request to submit your EIP, please use an abbreviated title in the filename, `eip-draft_title_abbrev.md`. The title should be 44 characters or less.-->

## Simple Summary

This EIP proposes a classification scheme for security weaknesses in smart contracts. 

## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->

The SWC is a smart contract specific software weakness classification scheme for developers, tool vendors and security practitioners. The SWC is loosely aligned to the terminologies and structure used in the [Common Weakness Enumeration - CWE](https://cwe.mitre.org) scheme while overlaying a wide range of weakness variants that are specific to smart contracts.

The goals of the SWC scheme are as follows:

- Provide a straight forward way to classify weaknesses in smart contract systems.
- Provide a straight forward way to specify the weakness(es) that lead to a vulnerability in a smart contract system. 
- Define a common language for describing weaknesses in smart contract systems' architecture, design, and code.
- Serve as a way to train and increase the performance of smart contract security analysis tools.


## Motivation
<!--The motivation is critical for EIPs that want to change the Ethereum protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EIP solves. EIP submissions without sufficient motivation may be rejected outright.-->

For years it's been widely accepted in the field of software security to use a common terminology and to classify security related bugs and errors with a standardized scheme. While this has not stopped vulnerabilities from appearing in software, it has helped communities focusing on web applications, network protocols, IOT devices and various other fields to educate users and developers to understand the nature of security related issues in their software. It has also allowed the security community to quickly understand vulnerabilities that occur in production systems to perform root causes analysis or triage findings from various security analysis tools. In recent years various organizations and companies also published vulnerability data to find the most widespread security issues based on collected vulnerability data. Two examples that are widely used and referred to are [SANS TOP 25 Most Dangerous Software Errors](https://www.sans.org/top25-software-errors) and the [OWASP TOP 10](https://www.owasp.org/index.php/Top_10-2017_Top_10). None of those publications would have been possible without common classification schemes. 

At present no such weakness classification scheme exists to identify weaknesses specific to Ethereum Smart Contracts. Common language and awareness of security weaknesses is mostly derived from best practice guides and from hacks that occurred on the main net. Findings from audit reports and security tool analysis add to the wide range of terminologies that is used to describe the discovered weaknesses. Often it's time consuming to understand the technical root cause and the risk associated to findings from different sources even for security experts. 

While recognizing the current gap, the SWC does not propose to reinvent the wheel in regards to classification of smart contract security weaknesses. It rather suggests to build on top of what has worked well in the other parts of the software security community and to adopt that into the world of smart contracts. From several software weakness classification schemes that exist currently, CWE stands out in terms of adoption and breadth of coverage. While CWE does not describe any weaknesses specific to smart contracts it does describe related weaknesses at higher abstraction layers. The EIP for SWC proposes to create smart contract specific variants while linking back to the larger spectrum of software errors that different platforms and technologies have in common. 

## Specification
<!--The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).-->


Before the SWC specification is discussed in detail it is important to describe the used terminologies in more detail:

- SWC ID: A numeric identifier linked to a variant (e.g. SWC-101).
- Weakness: A software error or mistake that in the right conditions can by itself or coupled with other weaknesses lead to a vulnerability. 
- Vulnerability: A weakness or multiple weaknesses which directly or indirectly lead to an undesirable state change in a smart contract system. 
- Variant: A specific weakness that is described in a very low detail specific to Ethereum smart contracts. Each variant is assigned an unique SWC ID.
- Base/Class: An abstract base description of a class of weaknesses. CWE has a wide range of base/class types that provide a meaningful hierarchal context for smart contract specific weakness variants. Every SWC ID is related to a Base or Class weakness type in the CWE.
- Test Case: A test case consist of a micro-sample or real-world vulnerable smart contract that demonstrates concrete instances of each SWC variant. Test cases serve as the basis for meaningful weakness classification and are useful to security analysis tool developers.

The SWC in its most basic form links a numeric identifier to a weakness variant. For example the identifier SWC-101 links to the _Integer Overflow and Underflow_ variant. It also links 

The following terminology is used throughout the SWC:




```
# Title 
Pick a meaningful title.

## Base/Class ID
Links a CWE base or class type to the variant. 
e.g.  [CWE-682 - Incorrect Calculation](https://cwe.mitre.org/data/definitions/682.html)

## Description 
Describes the nature and potential impact of the weakness on the contract system. 

## Remediation
Describes ways on how to fix the weakness. 

## References 
Link to external references that contain useful additional information on the issue.
```




Currently there is no common language to specify weaknesses in smart contracts. 



## Implementation
<!--The implementations must be completed before any EIP is given status "Final", but it need not be completed before the EIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->

The [Smart Contract Weakness Classification registry](https://github.com/SmartContractSecurity/SWC-registry) has been created on Github. 

All works in the repository licensed under GNU GPLv3. 

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
