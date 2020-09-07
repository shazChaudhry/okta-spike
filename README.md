# Objectives
Integrate Okta with Jenkins _(and with AWS in the future)_

## What is Okta?
It's an enterprise-grade, identity management service, built for the cloud, but compatible with many on-premises applications. With Okta, IT can manage any employee's access to any application or device. Okta runs in the cloud, on a secure, reliable, extensively audited platform, which integrates deeply with on-premises applications, directories, and identity management systems.

You can read all above Okta and what it does [here](https://support.okta.com/help/s/article/What-is-Okta?language=en_US)
- Documentation and support & sign up for a free Okta developer account: https://developer.okta.com/docs/

## Jenkins integration with Okta
- Vagrantfile is provided if you would like to use it as a throw away docker environment
- Deploy Jenkins and install plugins
  - `docker container run --rm --name jenkins -d -p 8080:8080 jenkins/jenkins:lts`
  - `docker container ls --latest` _(Check if Jenkins is up and running)_
  - `docker container logs -f jenkins` _(Jenkins' logs. Admin password will be visible)_
    - Retrieve Jenkins admin password in case you are not able to spot it in the console logs `docker container exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword` 
  - Navigate to http://[HOSTNAME]:8080 and follow on-screen instructions
  - Select suggested plugins. It will take a min or two to install the plugins
  - Install `SAML` & `Role-based Authorization Strategy` plug-ins and let Jenkins restart itself if it needs to
- Follow Okta-Jenkins-integration configurations described in this doc: [SAML Authentication with Okta SSO and users groups](https://rtfm.co.ua/en/jenkins-saml-authentication-via-okta-and-users-groups/#Okta_Community_Created_Jenkins_SAML_application)

## AWS integration with Okta _(future work)_
- Not tried yet but this document might be of help: https://help.okta.com/en/prod/Content/Topics/DeploymentGuides/AWS/aws-deployment.htm
- Not tried this doc either but might be of help: [How to Configure SAML 2.0 for AWS Account Federation](https://saml-doc.okta.com/SAML_Docs/How-to-Configure-SAML-2.0-for-Amazon-Web-Service#:~:text=IdP%2Dinitiated%20SSO-,Overview,and%20assign%20those%20to%20users.)

## References
- Okta website - https://www.okta.com/
- Understand SAML - https://developer.okta.com/docs/concepts/saml/
- Okta help centre: https://support.okta.com/help/s/