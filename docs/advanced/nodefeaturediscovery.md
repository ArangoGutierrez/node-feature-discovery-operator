---
title: "NodeFeatureDiscovery"
layout: default
sort: 2
---

# The NodeFeatureDiscovery CR

The `NodeFeatureDiscovery` CustomResource defines operational variables
to define the behaviour of the Node Feature Discovery Operand,
an example of the CustomResource:

```yaml
apiVersion: nfd.kubernetes.io/v1
kind: NodeFeatureDiscovery
metadata:
  name: nfd-master-server
  namespace: node-feature-discovery-operator
spec:
  operand:
    namespace: node-feature-discovery-operator
    image: k8s.gcr.io/nfd/node-feature-discovery:v0.7.0
    imagePullPolicy: Always
  workerConfig:
    configData: |
    #sources:
    #  cpu:
    #    cpuid:
    ##     NOTE: whitelist has priority over blacklist
    #      attributeBlacklist:
    #        - "BMI1"
    #        - "BMI2"
    #        - "CLMUL"
    #        - "CMOV"
    #        - "CX16"
    #        - "ERMS"
    #        - "F16C"
    #        - "HTT"
    #        - "LZCNT"
    #        - "MMX"
    #        - "MMXEXT"
    #        - "NX"
    #        - "POPCNT"
    #        - "RDRAND"
    #        - "RDSEED"
    #        - "RDTSCP"
    #        - "SGX"
    #        - "SSE"
    #        - "SSE2"
    #        - "SSE3"
    #        - "SSE4.1"
    #        - "SSE4.2"
    #        - "SSSE3"
    #      attributeWhitelist:
    #  kernel:
    #    kconfigFile: "/path/to/kconfig"
    #    configOpts:
    #      - "NO_HZ"
    #      - "X86"
    #      - "DMI"
    #  pci:
    #    deviceClassWhitelist:
    #      - "0200"
    #      - "03"
    #      - "12"
    #    deviceLabelFields:
    #      - "class"
    #      - "vendor"
    #      - "device"
    #      - "subsystem_vendor"
    #      - "subsystem_device"
    #  usb:
    #    deviceClassWhitelist:
    #      - "0e"
    #      - "ef"
    #      - "fe"
    #      - "ff"
    #    deviceLabelFields:
    #      - "class"
    #      - "vendor"
    #      - "device"
    #  custom:
    #    - name: "my.kernel.feature"
    #      matchOn:
    #        - loadedKMod: ["example_kmod1", "example_kmod2"]
    #    - name: "my.pci.feature"
    #      matchOn:
    #        - pciId:
    #            class: ["0200"]
    #            vendor: ["15b3"]
    #            device: ["1014", "1017"]
    #        - pciId :
    #            vendor: ["8086"]
    #            device: ["1000", "1100"]
    #    - name: "my.usb.feature"
    #      matchOn:
    #        - usbId:
    #          class: ["ff"]
    #          vendor: ["03e7"]
    #          device: ["2485"]
    #        - usbId:
    #          class: ["fe"]
    #          vendor: ["1a6e"]
    #          device: ["089a"]
    #    - name: "my.combined.feature"
    #      matchOn:
    #        - pciId:
    #            vendor: ["15b3"]
    #            device: ["1014", "1017"]
    #          loadedKMod : ["vendor_kmod1", "vendor_kmod2"]
```

For more information about how to setup the `WorkerConfig` stanza,
see
[worker config reference](https://kubernetes-sigs.github.io/node-feature-discovery/{{site.operand_version}}/advanced/worker-configuration-reference.html)