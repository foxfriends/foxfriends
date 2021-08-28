# Computer Security

An important part of any computer system is its *security*. Security relates to
ensuring that a system is resilient to attacks by malicious users, both external
users, and internal users, with access to the code. It is the work of the
@[software engineer][software-engineering] and the
@[software architect][software-architecture] to ensure that the system they are
building is secure.

A secure system must have all of three properties:
*   __Confidentiality__: the data can only be accessed by authorized parties
*   __Integrity__: the data is correct when it is accessed
*   __Availability__: the data is always available when it is needed

Related to computer security, but distinct, is @[computer privacy][].

Attacks may attempt to subvert any of those properties (e.g. read data that is
not meant to be accessible, trick other users into seeing incorrect data, or
simply take the whole system down).

Some types of attacks include:
*   @[SQL injection][]
*   @[Buffer overflow][]
