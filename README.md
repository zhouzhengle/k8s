

## helm
```bash
# 更新helm
brew install kubernetes-helm
```

## CCE接入datadog
### cce端配置
- 购买cce集群cce-demo
- 配置kubectl访问cce-demo集群
- 给每个node节点配置公网IP

### helm安装datadog-agent
```bash
# 添加第三方仓库
helm repo add datadog https://helm.datadoghq.com
helm repo update

# 安装datadog-agent
helm install datadog-agent -f datadog-values.yaml --set datadog.site='datadoghq.com' datadog/datadog
# 更新datadog-agent
helm upgrade -f datadog-values.yaml datadog-agent datadog/datadog
```
