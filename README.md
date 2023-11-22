# AWS-Route-53-Failover
Showcasing working knowledge of using Route 53 for failover purposes with web servers. 

Using the given architecture below. We configured our web server domain using Route 53 so that if the primary Availability Zone instance becomes unavailable,
Route 53 will automatically failover application traffic to the secondary Availability Zone's instance. 
![Screenshot 2023-11-21 at 3 47 41 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/e7b24e88-7c8c-45b0-af73-8594329a8491)

1) Confirm that there are two working EC2 insatnces deployed in different availability zones with different IP addresses.
![Screenshot 2023-11-21 at 3 53 07 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/5809467d-9c15-45db-a5ae-44278c2f4202)
![Screenshot 2023-11-21 at 3 53 56 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/6e868acd-3ac9-4924-aeb7-cda9d60e48e6)
2) Configure Route 53 Health Checks to sends emails when the health of an HTTP endpoint with a given IP address becomes unhealthy. Advance configuration options
were chosen to make the health check respond faster.
![Screenshot 2023-11-21 at 3 57 32 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/658abae7-03f8-441a-aa3e-fb1a843359ae)
3) Create an SNS topic to connected to the health check to send email notifications. 
![Screenshot 2023-11-21 at 3 59 50 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/81d6f6b5-51c4-4e96-8287-7a6fbe21af19)
4) Health Check Status
![Screenshot 2023-11-21 at 4 05 26 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/23d8c1c8-55d0-4cf7-a51d-77a1a231d1a1)
5) Create a failover record for the hosted zone and connect to the first CafeWebServer instance and connect to the primary health check. Do the same for the second CafeWebServer.
![Screenshot 2023-11-21 at 4 12 15 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/e8f524ec-b263-4083-9933-f0e5b500e57b)
![Screenshot 2023-11-21 at 4 14 20 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/e3283836-324a-4fda-a373-ec9d1134ddfb)
6) Verify Routing has taken place by ending EC2 instance, receiveing health check notifications, and routing of the webserver traffic although instance one is stopped.
![Screenshot 2023-11-21 at 4 20 20 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/3e88952f-2b64-4fbb-8b28-b20774db2aa8)
![Screenshot 2023-11-21 at 4 20 40 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/74083436-de09-48c7-a330-e579ce260bc5)
![Screenshot 2023-11-21 at 4 20 09 PM](https://github.com/jmckoy555/AWS-Route-53-Failover/assets/72049114/eb0c34be-3971-43bd-a241-81d679dc5f86)
