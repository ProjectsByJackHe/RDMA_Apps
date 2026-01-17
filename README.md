# What's this?

Here we have a list of applications leveraging NDv2 (Microsoft Network Direct: https://github.com/microsoft/NetworkDirect/tree/master/src) to interact with Network Adapters capable of RDMA on Windows.

As Network Direct is quite old, it has dependencies that can no longer be built due to deprecation. This project attempts to showcase usage of NetworkDirect today using modern Microsoft tooling.


# Building

Visual Studio 2022 + Desktop Development for C++, .NET desktop development.

I would recomend just using VSCode for development, but VS2022 is needed to manage
Nuget packages.

You also need msbuild, which is bundled with VS2022.
As soon as you download VS2022, just spawn a Developer Powershell and forget about it. CD into any project (like QueryNetAdapter), Run nuget restore, msbuild, and you're set.


# Use Case

You need the hardware capable of RDMA (obviously). Nvidia / Mellanox NICs are most common. You also need to own the topology.

Unlike other kernel bypass technologies like XDP, RDMA can only work in a LAN.

So the cables, NICs, switches all need to be specialized to make RDMA possible.

On Windows, SMB leverages RDMA on a best-effort basis. So use SMB to double check
first and foremost if your setup is good.

Once everything looks good, you will need the drivers that implement the NetworkDirect (NDv2) spec. This is vendor specific so you should look up what your NIC provider has published.

Once you confirm that you have the drivers that implement the NetworkDirect spec, finally you can start using the projects in this repo to interact with RDMA adapters.




