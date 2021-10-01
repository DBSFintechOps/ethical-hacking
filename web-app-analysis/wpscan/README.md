## WordPress Scan Tool wpscan

In order to use the wpscan tool, you need to have a webiste that is build on the Wordpress stack. An easy way to find websites that are build on wordpress is to use Google. Go to Google and in the search box add the following:

```shell
inurl:/wp-content
```

Hit enter, you should get back a huge amount of sites that have the /wp-admin path as part of their website. 

### Basic Scans
```shell
wpscan --url <WEBSITE_URL>
```
In some cases you may get a the following message:
```shell
Scan Aborted: The target is responding with a 403, this might be due to a WAF. Please re-try with --random-user-agent
```
This is most likely a Web Application Firewall blocking the request coming from wp-scan. To bypass it just add the random user agent flag as metioned above:
```shell
wpscan --url <WEBSITE_URL> --random-user-agent
```

### Scan for vulnerable themes & plugins

Basic scans will provide info on the plugins and their versions but will not show the associated vulnerabilities. In order to view these you need to register on the wpscan website -  https://wpscan.com/api. The free offering will do fine for local testing. Once you sign up you will receive an API key. Copy the API key provided from the https://wpscan.com/profile page. 
The new flags we will use:
<p>
<strong>e - enumerate</strong><br />
<strong>vp - vulnerable plugins</strong>
</p>

```shell
wpscan --url <WEBSITE_URL> -e vp --api-token <API_TOKEN>
```
This will however increase the time it takes for the scan. Expect it to be about 15 - 20 minutes in some cases. 

### Password Attacks

Check for any vulnerabilities around passwords on the WordPress site:

```shell
wpscan --url <WEBSITE_URL> -e u
```





