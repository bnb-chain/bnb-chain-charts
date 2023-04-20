# bnb-chain-charts
Helm chart repository for the bnb-chain.

It is a BNB Chain charts repository. So far, it is private helm chart repo. To use this Helm chart, you must first generate your private access token on GitHub.

## Add a repo

```
❯ helm repo add bnb-chain --username "$PAT_TOKEN" --password "$PAT_TOKEN" https://raw.githubusercontent.com/bnb-chain/bnb-chain-charts/gh-pages

"bnb-chain" has been added to your repositories
```

## Update helm repo

```
❯ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "bnb-chain" chart repository
Update Complete. ⎈Happy Helming!⎈
```

## Search repo bnb-chain

```
❯ helm search repo bnb-chain
NAME                    	CHART VERSION	APP VERSION	DESCRIPTION
bnb-chain/gnfd-validator	0.0.1        	           	A Helm chart for gnfd validator
```