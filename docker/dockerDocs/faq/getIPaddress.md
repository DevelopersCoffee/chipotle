    root@hhhh:/proc/2546# docker inspect 2623fbb3a275 -f '{{.   NetworkSettings.IPAddress}}'
    172.17.0.3
    
OR
    
    root@hhhh:/proc/2546# docker inspect 2623 | grep IPAddress
                "SecondaryIPAddresses": null,
                "IPAddress": "172.17.0.3",
                        "IPAddress": "172.17.0.3",