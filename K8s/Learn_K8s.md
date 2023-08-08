#To get currenrt context\
`kubectl config get-contexts`

#To set the devops-tools as default namespace\
`kubectl config set-context --current --namespace=devops-tools`

#Common kubernetes Commands\
`kubectl version`\
`kubectl version --short`\
`kubectl cluster-info`\
`kubectl get pods -n kube-system`\
`kubectl get pods -n kube-system -o wide`
