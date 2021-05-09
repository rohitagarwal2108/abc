
ELASTIC SEARCH WITH VPC

ELK_IAM_ROLE.yaml will create a role in IAM for elastic search so that it can access VPC.
Upload this template first in CFT.

ELK_WITH_VPC.yaml will create a ELASTICSEARCH in AWS with VPC.
Upload this template now in CFT.

This will create a IAM role and vpc network and Elastic search inside the VPC network.

To access Kibana link One has to launch a EC2 server within same VPC and subnet and same security group so that kibana link canbe accessed.We will create a tunnel with EC2 server with ELASTICSEARCH to access it.

Then launch a EC2 within same vc and subnet in which Elastic search got created and select the same sg also which is selected in ES then we have to create a tunnel to launch kibana .

keypair name : elkkeypair.pem

Type the below command in gitbash

ssh -i elkkeypair.pem ec2-user@52.14.211.218 -N -L 9200:vpc-ecstestpk-xrvgdsqnw6dclznr6lgfsj4vgu.us-east-2.es.amazonaws.com:443

This command will go infinite and it will not end.
in vpc-ecstestpk --> give your kibana link here so that tunnel can be created.

Go to browser and type below cmd
https://localhost:9200
https://localhost:9200/_plugin/kibana/

Now you can access the kibana link.

Refer the below doc for this : 

https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-vpc.html#es-vpc-security
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-elasticsearch-domain.html