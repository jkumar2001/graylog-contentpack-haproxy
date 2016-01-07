This content pack will launch an UDP input on port 11002 that is able to parse the standard HAProxy HTTPlogs.

http://cbonte.github.io/haproxy-dconv/configuration-1.5.html#8.2.3


Example log message:


      Feb  6 12:14:14 localhost \
      haproxy[14389]: 10.0.1.2:33317 [06/Feb/2009:12:14:14.655] http-in \
      static/srv1 10/0/30/69/109 200 2750 - - ---- 1/1/1/1/0 0/0 {1wt.eu} \
      {} "GET /index.html HTTP/1.1"

Will extract fields backend, frontend, http_version, message, remote_addr, request_past, request_verb, response_bytes, response_status, server, tc, tq, tr, tt, tw and timings.


Field   Format                                Extract from the example above

      1   process_name '[' pid ']:'                            haproxy[14389]:
      
      2   client_ip ':' client_port                             10.0.1.2:33317
      
      3   '[' accept_date ']'                       [06/Feb/2009:12:14:14.655]
      
      4   frontend_name                                                http-in
      
      5   backend_name '/' server_name                             static/srv1
      
      6   Tq '/' Tw '/' Tc '/' Tr '/' Tt*                       10/0/30/69/109
      
      7   status_code                                                      200
      
      8   bytes_read*                                                     2750
      
      9   captured_request_cookie                                            -
      
     10   captured_response_cookie                                           -
     
     11   termination_state                                               ----
     
     12   actconn '/' feconn '/' beconn '/' srv_conn '/' retries*    1/1/1/1/0
     
     13   srv_queue '/' backend_queue                                      0/0
     
     14   '{' captured_request_headers* '}'                   {haproxy.1wt.eu}
     
     15   '{' captured_response_headers* '}'                                {}
     
     16   '"' http_request '"'                      "GET /index.html HTTP/1.1"
     




Modified from https://github.com/Graylog2/graylog-contentpack-haproxy

Originally created by Daniel Kerwin (Gini GmbH).
