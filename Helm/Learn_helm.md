
## Learn Helm for K8s

#Create a helm chart:\
`helm create chart_name`

#Add a new helm repository:\
`helm repo add repository_name`

#List helm repositories:\
`helm repo list`

#Update helm repositories:\
`helm repo update`

#Delete a helm repository:\
`helm repo remove repository_name`

#Install a helm chart:\
`helm install name repository_name/chart_name`

#Download helm chart as a tar archive:\
`helm get chart_release_name`

#Update helm dependencies:\
`helm dependency update`

#Helm template validation without deployment: \
`helm install sxp-store --values=p13n-charts/environment/preprod/values.yaml --debug --dry-run p13n-charts/` \
`helm install <deployment-name> --values=<values.yaml file path in chart> --debug --dry-run <Chart-folder-name> `

#==========helm upgrade commands=========\
`helm upgrade -f new-values.yml {release name} {package name or path} --version {fixed-version}` \
`helm upgrade -f hodor-charts/environment/hyd_serving_prod/values.yml hodor-hyd hodor-charts --version` 

#+++++++ Helm Rollout ++++++++++++\

`helm uninstall hodor-serving-ch --keep-history`\

`helm rollback hodor-serving-ch 14`
