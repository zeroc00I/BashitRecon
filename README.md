# BashitRecon

#Filtro por Hosts Up

xargs -P 500 -a lista -I@ bash -c 'dig @ | grep NOERROR 1>/dev/null && echo | echo @;'
