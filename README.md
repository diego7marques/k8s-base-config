## Kubernetes Base config

:page_facing_up: The files available in this repository are part of [How to accelerate the Kubernetes cluster configuration using FluxCD – Part1
](https://containscloud.com/2024/04/26/how-to-accelerate-the-kubernetes-cluster-configuration-using-fluxcd-part1/) and [How to accelerate the Kubernetes cluster configuration using FluxCD – Part2
](https://containscloud.com/2024/05/17/how-to-accelerate-the-kubernetes-cluster-configuration-using-fluxcd-part2/) of [contains(cloud)](https://containscloud.com) ☁️ 

:computer: The EKS cluster used to this lab is available on: [EKS Lab Cluster](https://github.com/diego7marques/eks-lab-cluster)

Technologies used:

[![MySkills](https://skillicons.dev/icons?i=kubernetes)](#)

Thanks to [FluxCD](https://fluxcd.io/) project.

## How to install FluxCD using the repository code

1. Fork the repository

2. Run the following code changing the "owner":
```bash
### A PAT with read and write access to the repository must be provided.
export GITHUB_TOKEN=<myPAT> 

flux bootstrap github \
  --token-auth \
  --owner=<you> \
  --repository=k8s-base-config \
  --branch=main \
  --path=global-config \
  --personal
```

The result must be like:

![Installation](installation.gif)

## How to install specific components (crossplane example)
```bash
flux create kustomization crossplane \
    --source=GitRepository/flux-system \
    --path="./extra-capabitilies/crossplane-operator" \
    --prune=true \
    --interval=60m \
    --wait=true \
    --health-check-timeout=3m    
```

The result must be like:
![Installation](installing-specifics.gif)

## License

This code is licensed under the [MIT License](LICENSE).