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

This EIP proposes a classification scheme for security weaknesses in Ethereum smart contracts. 

## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->

The SWC is a smart contract specific software weakness classification scheme for developers, tool vendors and security practitioners. The SWC is loosely aligned to the terminologies and structure used in the [Common Weakness Enumeration - CWE](https://cwe.mitre.org) scheme while overlaying a wide range of weakness variants that are specific to smart contracts.

The goals of the SWC scheme are as follows:

- Provide a straightforward way to classify weaknesses in smart contract systems.
- Provide a straightforward way to identify the weakness(es) that lead to a vulnerability in a smart contract system. 
- Define a common language for describing weaknesses in smart contract systems' architecture, design and code.
- Train and increase the performance of smart contract security analysis tools.


## Motivation
<!--The motivation is critical for EIPs that want to change the Ethereum protocol. It should clearly explain why the existing protocol specification is inadequate to address the problem that the EIP solves. EIP submissions without sufficient motivation may be rejected outright.-->

In the software security industry, it is a widely accepted practice to use a common terminology and to classify security related bugs and errors with a standardized scheme. While this has not stopped vulnerabilities from appearing in software, it has helped communities focusing on web applications, network protocols, IOT devices and various other fields to educate users and developers to understand the nature of security related issues in their software. It has also allowed the security community to quickly understand vulnerabilities that occur in production systems to perform root cause analysis or triage findings from various security analysis sources. In recent years various organizations and companies also published vulnerability data to find the most widespread security issues based on collected vulnerability data. Two examples that are widely used and referred to are the [SANS TOP 25 Most Dangerous Software Errors](https://www.sans.org/top25-software-errors) and the [OWASP TOP 10](https://www.owasp.org/index.php/Top_10-2017_Top_10). None of those publications would have been possible without a common classification scheme. 

At present no such weakness classification scheme exists for weaknesses specific to Ethereum Smart Contracts. Common language and awareness of security weaknesses is mostly derived from academic papers, best practice guides and published articles. Findings from audit reports and security tool analysis add to the wide range of terminologies that is used to describe the discovered weaknesses. It is often time consuming to understand the technical root cause and the risk associated to findings from different sources even for security experts. 

## Rationale 

While recognizing the current gap, the SWC does not aim to reinvent the wheel in regards to classification of security weaknesses. It rather proposes to build on top of what has worked well in other parts of the software security community -  specifically the Common Weakness Enumeration (CWE), a list of software vulnerability types that stands out in terms of adoption and breadth of coverage. While CWE does not describe any weaknesses specific to smart contracts, it does describe related weaknesses at higher abstraction layers. This EIP proposes to create smart contract specific variants while linking back to the larger spectrum of software errors and mistakes listed in the CWE that different platforms and technologies have in common. 

## Specification
<!--The technical specification should describe the syntax and semantics of any new feature. The specification should be detailed enough to allow competing, interoperable implementations for any of the current Ethereum platforms (go-ethereum, parity, cpp-ethereum, ethereumj, ethereumjs, and [others](https://github.com/ethereum/wiki/wiki/Clients)).-->

Before discussing the SWC specification it is important to describe the terminology used:

- Weakness: A software error or mistake that in the right conditions can by itself or coupled with other weaknesses lead to a vulnerability. 
- Vulnerability: A weakness or multiple weaknesses which directly or indirectly lead to an undesirable state in a smart contract system. 
- Variant: A specific weakness that is described in a very low detail specific to Ethereum smart contracts. Each variant is assigned an unique SWC ID.
- Relationships: CWE has a wide range of _Base_ and _Class_ types that group weaknesses on higher abstraction layers. The CWE uses _Relationships_ to link SWC smart contract weakness variants to existing _Base_ or _Class_ CWE types. _Relationships_ are  used to provide context on how SWCs are linked to the wider group of software security weaknesses and to be able generate useful visualisations and insights through issue data sets. In its current revision it is proposed to link a SWC to its closest parent in the CWE. 
- SWC ID: A numeric identifier linked to a variant (e.g. SWC-101).
- Test Case: A test case constitutes a micro-sample or real-world smart contract that demonstrates concrete instances of one or multiple SWC variants. Test cases serve as the basis for meaningful weakness classification and are useful to security analysis tool developers. 

The SWC in its most basic form links a numeric identifier to a weakness variant. For example the identifier _SWC-101_ is linked to the _Integer Overflow and Underflow_ variant. While a list with the weakness title and a unique id is useful by itself, it would also be ambiguous without further details. Therefore the SWC recommends to add a definition and test cases to any weakness variant.

**SWC definition**  

A SWC definition is formated in markdown to allow good readability and tools to process them easily. It consists of the following attributes. 

- Title: A name for the weakness that points to the technical root cause.
- Relationships: Links a CWE _Base_ or _Class_ type to its CWE variant. The _Integer Overflow and Underflow_ variant for example is linked to [CWE-682 - Incorrect Calculation](https://cwe.mitre.org/data/definitions/682.html).
- Description: Describes the nature and potential impact of the weakness on the contract system. 
- Remediation: Describes ways on how to fix the weakness. 
- References: Links to external references that contain relevant additional information on the weakness.

**Test cases**

Test cases include crafted as well as real-world samples of vulnerable smart contracts. A single test case consists of three parts:

1. A smart contract sample containing zero or more weaknesses. 
2. A JSON file generated with solc that contains the byte code, AST and source code mappings. 
3. The YAML configuration file defining the types and number of weaknesses contained in the contract sample. Location information can be provided optionally through byte code offset as well as line numbers. Test case YAML configuration files can be verified with the following schema.

```YAML
description:
  type: string
  required: true
issues:
- id:
    type: string
    required: true
  count:
    type: number
    required: true
  locations:
  - bytecode_offsets:
    - type: number
    line_numbers:
    - type: number
```

## Implementation
<!--The implementations must be completed before any EIP is given status "Final", but it need not be completed before the EIP is accepted. While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->

The Smart Contract Weakness Classification registry located in this [Github repository](https://github.com/SmartContractSecurity/SWC-registry) uses the SWC scheme proposed in this EIP. A Github Pages rendered version is also available [here](https://smartcontractsecurity.github.io/SWC-registry/).

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
