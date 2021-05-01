# Managing a custom domain using Github Pages and AWS Route53

The easiest way to set this up is to use the subdomin you intend to host. In this case it was **www**. Read [this](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain) for a general rundown what you need to know/do.  

The steps to set this up in AWS is simple. Steps to follow are: 

- Step 1: Ensure you have registered your domain 
	- If AWS isn't your domain registrar (that is you bought your 
	domain via namecheap, google domains, etc), then you need to 
	figure out how to connect your domain on AWS. The steps for this 
	differ depending on your particular registrar so google around. 
	- for AWS, follow these steps (current as of 01/05/2021)
		- Step 1: Create a Hosted Zone in AWS Route 53 
			- Login into your AWS Management Console and head towards 
				Route 53 
			- Click Hosted zones > Click Create Hosted Zone 
			- Fill in Domain Name and select Type as Public Hosted 
				Zone and click create
	
- Step 2: Update Google Domain 
	- log into your Google Domains account
	- click on `My domains`
		- click on DNS 
		- under Name Servers, select Use Custom Name Servers 
		- Copy and paste all four Name Server (NS) from the Route 53 Record 
		- Sets panel and click save 
		- You should get a confirmation message like **Changes to 
			example.com saved. They'll take effect within the next 48 
			hours**. 

After registering your domain, implement the following steps:
	
	- add your domain name to CNAME file in one of two ways: 
	- via navigating to `Github Repo > Settings > Pages > Custom domain`
	- or cd'ing into the root of you repository and running:
		- `touch CNAME && echo "www.domain_name.com">>CNAME` 
	- Ensure that **Enforce HTTPS** is checked under `Settings > Pages`
	- Head to Route53 in AWS
		- selected hosted zone for the domain in question
		- click **create record**
		- fill out the fields to match the image below: 
			- [cname image](cname_aws_image.png)

