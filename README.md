# BashitRecon

#Filtering by up hosts

xargs -P 500 -a lista -I@ sh -c 'dig @ | grep NOERROR 1>/dev/null && echo | echo @;'

#Geting domains using reverse DNS

~Command
xargs -P 500 -a hosts -I@ sh -c 'dig @' 2>/dev/null | awk -F'<<>>' '{print $3}' | xargs -n1 | tee -a hosts

#Geting subdomains by ssl

Source: https://raw.githubusercontent.com/appsecco/the-art-of-subdomain-enumeration/master/san_subdomain_enum.py

~Command
xargs -P 100 -a hostUnicos -I@ sh -c 'sanssl @ 2>/dev/null | grep -v "No domains"'

#Getting subdomains by all Dns records and brute subdomain

~Command
dnsrecon -d alertmanager-1.staging.rtcdn.caffeine.tv -D /opt/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -t brt~
(Doest seems to be so useful)

~Command
altdns -t 600 -w /opt/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -i hostUnicos.txt -o hosts -r -s results_output.txt
