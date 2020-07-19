# BashitRecon

#Filtering by up hosts

xargs -P 500 -a lista -I@ sh -c 'dig @ | grep NOERROR 1>/dev/null && echo | echo @;'

#Get domains using reverse DNS

xargs -P 500 -a hosts -I@ sh -c 'dig @' 2>/dev/null | awk -F'<<>>' '{print $3}' | xargs -n1 | tee -a hosts
