# Create a snapshot {#concept_eps_gbl_xdb .concept}

A snapshot records the disk data state at a certain time point for data backup and image customization.

## Scenarios {#section_ewp_wyx_52b .section}

Creating a snapshot is essentially important. You can create a snapshot for data backup in advance in scenarios where operation risks exist. For example, you can create a snapshot if you need to modify critical system files, [migrate instances from a classic network to a VPC](../../../../../reseller.en-US/Best practices/Migrate from the classic network to VPC/Migration overview.md#), back up data routinely , prevent network attacks, [change the operating system](reseller.en-US/User Guide/Instances/Change the operating system.md#), or provide data support for a production environment.

Additionally, you can use a snapshot to [create customized images](reseller.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#) for quick application environment deployment in a large number of instances.

## Precautions {#section_azs_vyx_52b .section}

-   Creating a snapshot may slightly reduce disk performance and I/O performance. We recommend that you create a snapshot during off-peak hours.
-   A snapshot only records data at a certain time point. Therefore, incremental data generated by disk operations during snapshot creation is not synchronized to a created snapshot.
-   To guarantee successful snapshot creation, you cannot modify the ECS instance status, for example, by stopping or restarting the instance, during snapshot creation.
-   When you create a snapshot based on an instance, the instance must be in **Running** or **Stopped** status.
-   When you create a snapshot based on a disk, the disk must be in **Running** status.
-   Manually created snapshots will always exist unless you delete them. Therefore, you need to [delete unnecessary snapshot](reseller.en-US/User Guide/Snapshots/Delete snapshots or automatic snapshot policies.md#) to prevent continuous deduction caused by increasing snapshot capacity.
-   If you create an extended volume by using a multi-partition single disk, the snapshots you created can be used for [rolling back a cloud disk](reseller.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#).
-   After you create a dynamic extended volume by using multiple disks and no I/O operation is performed on data in the extended volume, the snapshot you created can be used for disk rollback. If I/O operations are continuously performed in the extended volume, data consistency of the rolled-back disk is unsure.

## Procedure {#section_pdn_xdl_xdb .section}

To create a snapshot on the ECS console, do the following:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  Select a region.
3.  In the left navigation pane, click **Instances**.
4.  Locate the instance which you want to create a snapshot for and click **Manage**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/15420248949505_en-US.png)

5.  In the left navigation pane, click **Disks**. In the refreshed right pane, locate the target disk and click **Create Snapshot**. You can select only one disk at a time. **Type** can be either system disk or data disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/15420248944530_en-US.png)

6.  Enter the snapshot name and click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/15420248944550_en-US.png)

7.  In the left navigation pane, click **Instance Snapshots**. You can see the progress, estimated remaining time, and status of the snapshot.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/15420248944552_en-US.png)


Alternatively, you can use the ECS API [CreateSnapshot](../reseller.en-US/API Reference/Snapshots/CreateSnapshot.md#) to create a snapshot.

## Time required {#section_gvs_ydl_xdb .section}

The time required for creating a snapshot depends on the disk capacity.

According to the [incremental snapshot mechanism](../reseller.en-US/Product Introduction/Snapshots/Incremental snapshot mechanism.md#), the first disk snapshot records full disk data and takes a long time. The next snapshot can be created in a shorter time. However, the exact time required depends on the amount of data generated since the first snapshot creation. The larger the data amount is, the longer time the snapshot creation will take.

## What to do next {#section_mx4_cyy_52b .section}

After you create a snapshot, you can proceed with the following:

-   [Roll back a cloud disk](reseller.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#)
-   [Create a cloud disk from a snapshot](reseller.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#)
-   [Create a custom image by using a snapshot](reseller.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#)

