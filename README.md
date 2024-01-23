This repository has been created for MTA-STS policy configuration

# What is MTA-STS?

Emails crossing the internet use secure connections encrypted using Transport Layer Security (TLS). However, there remain vulnerabilities in this method of protecting the confidentiality of emails, 
whereby a person-in-the-middle can trick incoming connections to send to another server and/or send information in the clear. MTA-STS is a standard designed to address these vulnerabilities.

As per the document https://www.security.gov.uk/guidance/email-guidance/mta-sts/set-up; we need to create an MTA-STS policy file (a .txt file). The policy file must be publicly readable by HTTPS so it will need a certificate.
We are using godaddy.com & webflow for Domain and host website resources, we were not able to find the posibility to host policy file through neither godaddy nor webflow. That why we had decided to Host MTA-STS policy using GitHub Pages 
by following the article https://eightwone.com/2023/10/05/hosting-mta-sts-policy-using-github-pages/.

# Steps followed for the configuration

1. Create a new repository 'expian-policy' in GitHub and make sure it's public.
2. Create an empty file '.nojekyll' in the repository. This file will instruct GitHub not to build pages, and just serve your files.
3. Create the policy file that needs to be named 'mta-sts.txt' in the .well-known folder file.
4. We need to enable GitHub Pages for this repository. Go to Settings, and select the Pages tab. Under Branch, select the branch you want to publish, eg. main, and press Save. 
5. On GitHub page settings update custom domain as 'mta-sts.expian.io'and then created a CNAME record 'mta-sts' with Data value 'ticknovate.github.io.', TXT record '_mta-sts' with Data value 'v=STSv1; id=20231222'.
6. The Mode in Policy should be 'testing' after 2 weeks if there are no issue in email delivery then update the Mode to 'enforce'.
