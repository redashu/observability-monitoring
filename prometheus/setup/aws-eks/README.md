## Using mac OS 

### EKSCTL 

## Installing eksctl on mac os 

### Step 1

<i> Adding Repo </i>
```
 brew tap weaveworks/tap

```

### Step 2 

<i> Installing eksctl </i>

```
brew install eksctl

```

### step 3 -- Verify 

```
setup git:(master) ✗ eksctl version 
0.158.0-dev+4a0ee7154.2023-09-22T12:23:54Z

```

### step 4 -- Creating cluster using eksctl 

### setup.yaml

```
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: ashu-cluster
  region: ap-south-1

nodeGroups:
  - name: linux-nodes
    instanceType: t2.small
    minSize: 0
    maxSize: 5

```

### creating eks cluster -- This will take time around 20 minutes

```
eksctl create cluster -f  eks_setup.yaml
```

