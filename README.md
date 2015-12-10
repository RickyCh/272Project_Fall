Compliance management has become a primitive objective of any organisation that wants to host
data/customer data on public cloud/private cloud. Security standards like PCI,HIPAA and NIST
have been analysed in this project with case studies on each of their control objectives,
requirements. Existing solutions provide efficient strategies for compliance management,
monitoring and real time analytics at a considerable cost. Solutions do not cover the real time
analytics at a per activity basis from the aggregated logs. This has been identified as one of the
challenges of our project which also differentiates our project’s deliverable from available
solutions in the market. An unusual activity could be a possible threat leading to meet
requirements of a particular compliance. For instance, any change in rules/packet filters of
firewall can enable a hacker to access servers and launching attacks. This activity of changing
rules can be considered as an unusual activity as it may cause deviation from regulations
imposed by a standard, PCI in this case. Mapping of deviation to a possible compliance breach is a
main feature of our project along with real time analytics. Deviation detections and
recommendation engine is responsible for vulnerability predictions, penetration testing in a time
and cost efficient manner.

Every user in Access control lists(ACL), as a security descriptor has been identified as a class of
stakeholder from the enterprise perspective. CIO(chief information officer) of a company might
want to get an overall view of compliance status while a security administrator might want to
drill down to detected threats, deviations from compliance standards and use the
recommendation provided by the compliance manager to achieve better compliance. From
these user stories, we have built different views of the underlying data and customised the front
end for better analysis from stakeholders point of view. We have ensured that data visualisation,
deviation detection and recommendation work in real time efficiently as well as provide specific
and accurate notifications in low cost.
Backend infrastructure consists of AWS instances for log aggregation and processing. Data
analytics was done with SparkSQL and Elastic search with the following considerations :-

❖ How does a particular activity affect compliance status?
Mar 1 06:25:43 server1 Accepted publickey sshd[23170]: Accepted publickey for server2 from
172.30.128.115 port 21011 ssh2
This log message could mean that hacker gained access to the server that was not supposeddly
exposed for public access. If the attempt was successful, data could be exposed leading to
compliance and security threat.

❖ What is cloud compliance and how are log messages helping us?HIPAA rules and regulations mentions “ ​
Access authorization ​
” under administrative safeguards
and the solution is to implement policies and procedures for granting access to electronic
protected health information, for example, through access to a workstation, transaction, program,
process, or other mechanism. PCI DSS requirements states that “ ​
Restrict access to cardholder
data by business need-to-know” and the control objective is to implement strong access and
control measures. These requirements essentially mean that the server needs to be protected
from public access and hence if an unknown server accepts public key, it could possibly lead to
compliance breach. Our backend analysis consisting of Spark and Elastic Search uses query
strings like “accepted public key” , “illegal user” to tag these log messages under a possible
compliance breach. We have used map-reduce algorithm to map each of these activities to a
specific compliance. ELT( Extract- Load-Transform) model has been adapted with EC2 instances
performing extraction, GrayLog and Elastic Search performing the loading, SparkSQL performing
the transformation using map-reduce.

❖ What does the Compliance Manager do?
Based on aggregated logs and backend analytics, we have customised a user friendly Front End
interface written in javascript. Our project currently implements compliance status for PCI,
HIPAA and NIST for every stakeholder as discussed above. For every unusual activity, we have
tags under compliance(single/multiple) violation and vulnerability prediction based on analysis
of log message. Recommendation engine provides alerts and recommendations based on
deviations detected and notifies the user. From a time perspective, we have customised our
dashboard to showcase compliance status, alerts, recommendations and vulnerability
predictions.
