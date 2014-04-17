## ZONE01: Fully qualified master nameserver in SOA

### Test case identifier
**ZONE01** Fully qualified master nameserver in SOA

### Objective

The SOA MNAME record must be a fully qualified master nameserver.
Hostnames are valid according to the
rules defined in [RFC 952](http://tools.ietf.org/html/rfc952),
section 3.3.13 in [RFC 1035](http://tools.ietf.org/html/rfc1035)
and section 11 in [RFC 2182](http://tools.ietf.org/html/rfc2181#section-11).
The hostname of the MNAME field may not be listed among the delegated
name servers, but should still be authoritative for the zone. MNAME may
be used for other services such as DNS NOTIFY described in
[RFC 1996](http://tools.ietf.org/html/rfc1996).

### Inputs

The domain name to be tested.

### Ordered description of steps to be taken to execute the test case

1. Retrieve the SOA record from the zone being tested.
2. If the SOA MNAME field does not exist in DNS, this text case fails.
3. If the IP addresses for the SOA MNAME field does not answer DNS queries
   this test case fails.
4. If the SOA MNAME field is not authoritative for the zone tested,
   this test case fails.
5. If the SOA MNAME field is not part of the NS set for the zone, this
   test case may yield a notice message.

### Outcome(s)

If the SOA MNAME field is not an authoritative DNS server for the domain name,
this test case fails.

### Special procedural requirements

None.

### Intercase dependencies

The syntax of the SOA MNAME field is tested in [SYNTAX07](../Syntax-TP/syntax07.md).