# Update an instance group

After creating an instance group, you can:

- [Change its name and description](#change-name).
- [Change the computing resources](#change-compute-resources).
- [Increase the disk size](#change-disk-size).

## Changing the name and description {#change-name}

To change the name and description of an instance group:

{% list tabs %}

- Management console

  1. Open the folder page in the management console.
  1. Select **{{ compute-full-name }}**.
  1. On the **Virtual machines** page, go to the **Instance groups** tab.
  1. Click on the name of the group you want to update.
  1. Click **Change** in the upper-right corner of the page.
  1. Enter the appropriate name and description for the group.
  1. Click **Save**.

- CLI

  {% include [cli-install.md](../../../_includes/cli-install.md) %}

  {% include [default-catalogue.md](../../../_includes/default-catalogue.md) %}

  1. See the description of the CLI's update group command:

     ```
     $ yc compute instance-group update --help
     ```

  1. Get a list of instance groups in the default folder:

      {% include [instance-group-list.md](../../../_includes/instance-groups/instance-group-list.md) %}

  1. Select the `ID` or `NAME` of the necessary group (for example, `first-instance-group`).

  1. Specify the appropriate name and description in the YAML file that was used to create the group (for example, `template.yaml`). If the YAML file wasn't saved, [get information](get-info.md) about the instance group and create a new file. For more information, see [{#T}](create-fixed-group.md).

  1. Update the instance group in the default folder:

      ```
      $ yc compute instance-group update --name first-instance-group --file template.yaml
      ```

     {{ ig-name }} starts the operation to update the instance group.

- API

  You can change the group name and description using the [update](../../../_api-ref/compute/api-ref/InstanceGroup/update.md) API method.

  To request a list of available groups, use the [listInstances](../../../_api-ref/compute/api-ref/InstanceGroup/listInstances.md) method.

{% endlist %}

## Changing computing resources {#change-compute-resources}

After creating an instance group, you can change:

- The core usage type (partial or full).
- The number of vCPUs and amount of RAM.

To change the computing resources of an instance group:

{% list tabs %}

- Management console

  1. Open the folder page in the management console.
  1. Select **{{ compute-full-name }}**.
  1. On the **Virtual machines** page, go to the **Instance groups** tab.
  1. Click on the name of the group you want to update.
  1. Click **Change** in the upper-right corner of the page.
  1. Delete the current instance template and create a new one with the appropriate instance parameters.
  1. Click **Save**.

- CLI

  {% include [cli-install.md](../../../_includes/cli-install.md) %}

  {% include [default-catalogue.md](../../../_includes/default-catalogue.md) %}

  1. See the description of the CLI's update group command:

     ```
     $ yc compute instance-group update --help
     ```

  1. Get a list of instance groups in the default folder:

      {% include [instance-group-list.md](../../../_includes/instance-groups/instance-group-list.md) %}

  1. Select the `ID` or `NAME` of the necessary group (for example, `first-instance-group`).

  1. Specify the necessary instance parameters in the `resources_spec` key in the YAML file that was used to create the group (for example, `template.yaml`). If the YAML file wasn't saved, [get information](get-info.md) about the instance group and create a new file. For more information, see the section [{#T}](create-fixed-group.md).

  1. Update the instance group in the default folder:

      ```
      $ yc compute instance-group update --name first-instance-group --file template.yaml
      ```

     {{ ig-name }} starts the operation to update the instance group.

- API

  You can change the computing resources using the [update](../../../_api-ref/compute/api-ref/InstanceGroup/update.md) API method.

  To request a list of available groups, use the [listInstances](../../../_api-ref/compute/api-ref/InstanceGroup/listInstances.md) method.

{% endlist %}

## Increasing the disk size {#change-disk-size}

To increase the disk size of an instance group:

{% list tabs %}

- Management console

  1. Open the folder page in the management console.
  1. Select **{{ compute-full-name }}**.
  1. On the **Virtual machines** page, go to the **Instance groups** tab.
  1. Click on the name of the group you want to update.
  1. Click **Change** in the upper-right corner of the page.
  1. In the **Disks** section, specify the disk size:
  1. Click **Save**.

- CLI

  {% include [cli-install.md](../../../_includes/cli-install.md) %}

  {% include [default-catalogue.md](../../../_includes/default-catalogue.md) %}

  1. See the description of the CLI's update group command:

     ```
     $ yc compute instance-group update --help
     ```

  1. Get a list of instance groups in the default folder:

      {% include [instance-group-list.md](../../../_includes/instance-groups/instance-group-list.md) %}

  1. Select the `ID` or `NAME` of the necessary group (for example, `first-instance-group`).

  1. Specify the required storage size in the `boot_disk_spec` key in the YAML file that was used to create the group (for example, `template.yaml`). If the YAML file wasn't saved, [get information](get-info.md) about the instance group and create a new file. For more information, see the section [{#T}](create-fixed-group.md).

  1. Update the instance group in the default folder:

      ```
      $ yc compute instance-group update --name first-instance-group --file template.yaml
      ```

     {{ ig-name }} starts the operation to update the instance group.

- API

  You can change the disk size using the [update](../../../_api-ref/compute/api-ref/InstanceGroup/update.md) API method.

  To request a list of available groups, use the [listInstances](../../../_api-ref/compute/api-ref/InstanceGroup/listInstances.md) method.

{% endlist %}

