# Change the CentOS 6 source address

CentOS 6 has reached end-of-life \(EOL\), and the Linux community no longer maintains this operating system version. We recommend that you upgrade your operating system to CentOS 7 or later. If you still require some of the installation packages of CentOS 6 during the transition, you can change the CentOS 6 source address for your images as instructed in this topic.

CentOS 6 has reached EOL as of November 30th, 2020. In accordance with the community rules of Linux, the content under the source address `http://mirror.centos.org/centos-6/` of CentOS 6 has been removed. All third-party image providers have already removed the CentOS 6 source address. The `http://mirrors.cloud.aliyuncs.com` and `http://mirrors.aliyun.com` source addresses of Alibaba Cloud cannot synchronize with the CentOS 6 source address. If you continue to use the default CentOS 6 source address on Alibaba Cloud, an error is reported. The following figure shows an example of the error.

![centos 6 error](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4328707061/p187588.png)

You can perform the following steps to change the source address configurations in the CentOS 6 operating system based on the network environment.

-   For VPC-type instances, you must change to `http://mirrors.cloud.aliyuncs.com/centos-vault/6.10/`.
-   For classic network-type instances, you must change to `http://mirrors.aliyuncs.com/centos-vault/6.10/`.

1.  Connect to an ECS instance that runs CentOS 6.

    For more information, see [Overview](/intl.en-US/Instance/Connect to instances/Overview.md).

2.  Run the following command to modify the `CentOS-Base.repo` file:

    ```
    vim /etc/yum.repos.d/CentOS-Base.repo 
    ```

3.  Press the I key to enter the edit mode. Modify the following content to change the source address.

    Modify the file content based on the network type of the instance.

    -   VPC

        ```
        [base]
        name=CentOS-6.10
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.cloud.aliyuncs.com/centos-vault/6.10/os/$basearch/
        gpgcheck=1
        gpgkey=http://mirrors.cloud.aliyuncs.com/centos-vault/RPM-GPG-KEY-CentOS-6
        
        [updates]
        name=CentOS-6.10
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.cloud.aliyuncs.com/centos-vault/6.10/updates/$basearch/
        gpgcheck=1
        gpgkey=http://mirrors.cloud.aliyuncs.com/centos-vault/RPM-GPG-KEY-CentOS-6
        
        [extras]
        name=CentOS-6.10
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.cloud.aliyuncs.com/centos-vault/6.10/extras/$basearch/
        gpgcheck=1
        gpgkey=http://mirrors.cloud.aliyuncs.com/centos-vault/RPM-GPG-KEY-CentOS-6
        ```

    -   Classic network

        ```
        [base]
        name=CentOS-6.10
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.aliyuncs.com/centos-vault/6.10/os/$basearch/
        gpgcheck=1
        gpgkey=http://mirrors.aliyuncs.com/centos-vault/RPM-GPG-KEY-CentOS-6
        
        [updates]
        name=CentOS-6.10
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.aliyuncs.com/centos-vault/6.10/updates/$basearch/
        gpgcheck=1
        gpgkey=http://mirrors.aliyuncs.comm/centos-vault/RPM-GPG-KEY-CentOS-6
        
        [extras]
        name=CentOS-6.10
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.aliyuncs.com/centos-vault/6.10/extras/$basearch/
        gpgcheck=1
        gpgkey=http://mirrors.aliyuncs.com/centos-vault/RPM-GPG-KEY-CentOS-6
        ```

    After you modify the file content, press the Esc key to exit the edit mode and enter `:wq` to save and close the file.

4.  Run the following command to modify the `epel.repo` file:

    ```
    vim /etc/yum.repos.d/epel.repo
    ```

5.  Press the I key to enter the edit mode. Modify the following content to change the source address.

    Modify the file content based on the network type of the instance.

    -   VPC

        ```
        [epel]
        name=Extra Packages for Enterprise Linux 6 - $basearch
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.cloud.aliyuncs.com/epel-archive/6/$basearch
        gpgcheck=0
        gpgkey=http://mirrors.cloud.aliyuncs.com/epel-archive/RPM-GPG-KEY-EPEL-6
        ```

    -   Classic network

        ```
        [epel]
        name=Extra Packages for Enterprise Linux 6 - $basearch
        enabled=1
        failovermethod=priority
        baseurl=http://mirrors.aliyuncs.com/epel-archive/6/$basearch
        gpgcheck=0
        gpgkey=http://mirrors.aliyuncs.com/epel-archive/RPM-GPG-KEY-EPEL-6
        ```

    After you modify the file content, press the Esc key to exit the edit mode and enter `:wq` to save and close the file.

6.  After you change the source address, run the yum install command to install the required software packages.


**Related topics**  


[CentOS Product Specifications](https://wiki.centos.org/About/Product)

