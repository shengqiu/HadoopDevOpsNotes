# 3 Roles:
- client
- server
- KDC


# Steps
1. get initial ticket
- client send client key to KDC, 
- the Ticket-Genrating Service on the KDC create TGT(ticket-generating ticket)
- KDC encrypt the TGT using client key
- client get the ticket and decrypt using client key

2. get service ticket and access service
- cilent send ticket and service request to KDC
- KDC generates a session key for the server and client, and pack this session key with user credential, expiration time, ip address in a service ticket
- KDC encrpyt the service ticket using the the service key and send this to client
- client get the service ticket and send this to server
- server uses the service ticket to get all.


