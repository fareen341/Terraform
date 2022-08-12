<h1>Terraform</h1>
<pre>
<b>Limitation of on prem data center:</b>
flow: on prem data center
BA(business analyst) -> BRD(functional doc) SA/Tech -> HLD/LLD(high/low level doc) -> Work is distributed -> give to procurement team -> Buy(hardware) which will takes months of time -> data center -> ops team

ops will involved teams system admins, N/W admin, storage, backup, application team will be involved in it.
We might have error in all these process.

problem: Managing, upgrading infrastructure is problem.

<b>To solve all these problems we can use CLOUD</b>

Still on cloud serial execution meaning from developemet to build to QA to stage to production is taking a lot of time.
So for all these we write complex shell script, powershell script(for windows) for this CI/CD process.

Organigation wants to find an automation tool to automate all these.

<b>How to automate infrastructure?</b>
In AWS we've cloudformation using which i can create infrastructure with the help of script json/yml. Running the script only once will create many machines. But Cloudformation is only in AWS. We can also use ansible(used for install and manage the appln, configuration mgmt tool). Ansible is better for existing infrastructure, changes/modifictaion can be done in existing infrastructure.
Ansible can also be used as IAC. 

Cloudformation is very good for IAC but it's only for AWS so for other cloud we can use Terraform(specially design for provesioning infrastructure) that's why it is also called as provesioning tool. It can create infrastructure on any cloud, on prem DS it's not plateform dependent. Using declarative language as in declare we need 10 servers.

To automate infrastructure.
IAC(Infrastructure as code) tool.
No need to manually create infrastructure.

<b>Terraform is:</b>
1)Open source
2)Not platform
3)Using declarative language which is easy(they defined there own language named HCL(Hashcorm Language)).
4)Installation is very easy(only one binary installation).

Terraform and ansible is overlapping with each other.
Terraform is v good in infrastructure and ansible is v good for deploying so use terraform for infrastructure and ansible for deploying.

Can also replicate infrastructre is easy with the help of terraform. Readily available service is cloudfromation in AWS.

<b>HCL language</b>
.tf file created
Each time changes happen it adjust itself any number of time as in create 100 severs changed to 50 servers etc. Same script can be re-utilized.
Easy to understand, few lines of code, readable, declarative

<b>How terraform works</b>
Terraform script is given as input to Terraform core. Terraform alwas look for current state of the infrastructure as in if i have 7 servers it'll look the current state of the infrastructure. 
Terraform core look for needed infrastructure.
If i have declare 10 servers terraform will look for current state and see 7 servers are already present so it'll create 3 servers only. 
It also have providers.


<b>Downloading terraform</b>
On official website run the given command or copy the AMD64 binary file.

Step 1:
Binary file:
$ wget paste binary_file

Step 2: unzip
$ unzip terraform_TAB

Step 3: copy terraform to /user/local/bin
$ mv terraform /usr/local/bin/

Step 4: ls - l /usr/local/bin/

Done with configuration of terraform

To check it is installed and configured successfully:
$ terraform version

init -> plan -> apply , terraform process.
To create a resource we need one of the providers from the terraform registry(registry.terraform.io)


Sample terraform file:

Step 1:
local.tf

//creating file locally not on remote server as in AWS, without provides terraform won't understand what to do.
provider "local"{
	
}

resource "local_file" "cloudbots" {
	content = "Hello cloudbots..v1!!"
	filename = "cloudbots.txt"
} 

Step 2:
$ terraform init
It'll understand the local conf file and it'll go to provider section and it'll see which provider you're looking for.
 
Step 3:
$ terraform plan
// it'll create a file locally

Step 4: 
$ terraform apply
Enter a value: yes

o/p: local file named cloudbots.txt created

//will return the current states of all the .tf files we have 
$ terraform refresh

To destroy
$ terraform destroy
Enter a value: yes

o/p: it'll destroy infrastructure
it'll destroy the ec2 instance created

Each provides will have many resource types amd we need to find which resource type we need as in EC2 will be the provider and it'll have many resources as in ec2, s3 ...etc, so to create ec2 instance we'll use "aws_instance" resource type

<b>Example 2:</b>
Aws create instance:
Terraform official documentation have given the examples

In the example if we have given 100 machines to create then it'd be creating 100 machines in the same amount of time which it takes to create one, it'll take few seconds only.

</pre>

<h3>Extra</h3>
<pre>
1)Used for creating infrastructure.
2)Terraform can decide how many no. of servers needed and how many can be reduced thus reducing the business costs.
3)It can create the entire infrastructure in hours/minutes.
4)Usefull for managing infrastructure.
5)It compares the new infrastructure with the existing infrastructure and decide how many servers need etc.
</pre>

