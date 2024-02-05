# self_k8s
Свой k8s на VM
устанавливаем кластер кубспреем (v2.19.0)

`ansible-playbook -i inventory/k8s/hosts.yaml cluster.yml`

устанавливаем metallb

https://metallb.universe.tf/installation/

`kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.3/config/manifests/metallb-native.yaml`

редактируем и применяем `pool-1.yml` - пул IP (Свободные не занятые адреса)

`kubectl apply -f pool-1.yml`

редактируем и применяем `l2advertisement.yml` - необходимо поправить название пула - `first-pool`

`kubectl apply -f l2advertisement.yml`

установка ингресс (версия важна) 

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.0.4/deploy/static/provider/cloud/deploy.yaml`

далее проверяяем работу ингреса

`cd test_ingress`

`kubectl apply -f apple.yaml && kubectl apply -f ingress.yaml`\
