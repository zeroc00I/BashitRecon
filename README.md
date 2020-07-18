# BashitRecon

#Filtro por Hosts Up
xargs -P 500 -a listaHosts -I@ bash -c 'a=$(dig +short @ | wc -l); [[ $a -gt 0 ]] && echo @;'
