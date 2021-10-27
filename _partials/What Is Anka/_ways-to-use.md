## Using Anka

### Registry Only

This setup requires:

1. At least one Anka Node (macOS host running the Anka Virtualization software).
2. A linux container running the Anka Build Cloud Registry.
3. Your CI/CD's runner/agent installed and able to execute `anka` CLI commands to prepare and use the Anka VM. For example, install the github actions runner and then use [our action]({{< relref "intel/CI Plugins and Integrations/GitHub Actions/_index.md" >}}).

![Controller-less]({{< siteurl >}}images/what-is-anka/AWS_AnkaBuildController-lessDiagram.png)

### Controller + Registry (Build Cloud)

This setup requires:

1. At least one Anka Node (macOS host running the Anka Virtualization software).
2. A linux container running the Anka Build Cloud Controller & Registry.
3. Our plugin installed in your CI/CD tool (like the [Anka Jenkins Plugin]({{< relref "intel/CI Plugins and Integrations/Jenkins/_index.md" >}})). See a full list of plugins available on our [CI Plugins and Integrations]({{< relref "intel/CI Plugins and Integrations/_index.md" >}}) page.

![Controller+Registry]({{< siteurl >}}images/what-is-anka/AWS_AnkaBuildDiagram.png)