---
title: "Post: Notice"
classes: wide
categories:
  - Blog
tags:
  - Post Formats
  - notice
---

A notice displays information that explains nearby content. Often used to call attention to a particular detail.

When using Kramdown `{: .notice}` can be added after a sentence to assign the `.notice` to the `<p></p>` element.

**Changes in Service:** We just updated our [privacy policy](#) here to better service our customers. We recommend reviewing the changes.
{: .notice}

**Primary Notice:** Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. [Praesent libero](#). Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet.
{: .notice--primary}

**Info Notice:** Lorem ipsum dolor sit amet, [consectetur adipiscing elit](#). Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet.
{: .notice--info}

**Warning Notice:** Lorem ipsum dolor sit amet, consectetur adipiscing elit. [Integer nec odio](#). Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet.
{: .notice--warning}

**Danger Notice:** Lorem ipsum dolor sit amet, [consectetur adipiscing](#) elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet.
{: .notice--danger}

**Success Notice:** Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at [nibh elementum](#) imperdiet.
{: .notice--success}

Jekyll Rouge Highlight Tag

{% highlight hcl linenos %}
locals {
  address_spaces = zipmap(var.regions, var.address_spaces)

  firewall_tags = merge(local.tags, {
    "role" = "hub_firewall"
  })

  network_tags = merge(local.tags, {
    "role" = "hub_virtual_network"
  })

  hub_virtual_networks = {
    for r in var.regions : r => {
      address_space                   = [local.address_spaces[r]]
      name                            = module.naming[r].firewall.name
      location                        = azurerm_resource_group.hub[r].location
      resource_group_name             = azurerm_resource_group.hub[r].name
      resource_group_lock_enabled     = false
      resource_group_creation_enabled = false
      mesh_peering_enabled            = true
      routing_address_space           = [local.address_spaces[r]]
      tags                            = local.network_tags
      hub_router_ip_address           = "1.2.3.4"
      #flow_timeout_in_minutes          = 4
      subnets = {
        # The module will currently fail attempting to attach a route table to AzureBastionSubnet
        AzureBastionSubnet = {
          address_prefixes             = [module.subnet_addressing[r].network_cidr_blocks["AzureBastionSubnet"]]
          assign_generated_route_table = false
        }
        ServiceNowVMs = {
          address_prefixes = [module.subnet_addressing[r].network_cidr_blocks["ServiceNowVM"]]
        }
      }
      # firewall = {
      #   sku_name              = "AZFW_VNet"
      #   sku_tier              = "Standard"
      #   threat_intel_mode     = "Off"
      #   subnet_address_prefix = module.subnet_addressing[r].network_cidr_blocks["AzureFirewallSubnet"]
      #   firewall_policy_id    = azurerm_firewall_policy.fwpolicy.id
      #   tags                  = local.firewall_tags
      # }
    }
  }
}
{% endhighlight %}

Github Flavored Markdown Fenced Code Blocks
```hcl
locals {
  address_spaces = zipmap(var.regions, var.address_spaces)

  firewall_tags = merge(local.tags, {
    "role" = "hub_firewall"
  })

  network_tags = merge(local.tags, {
    "role" = "hub_virtual_network"
  })

  hub_virtual_networks = {
    for r in var.regions : r => {
      address_space                   = [local.address_spaces[r]]
      name                            = module.naming[r].firewall.name
      location                        = azurerm_resource_group.hub[r].location
      resource_group_name             = azurerm_resource_group.hub[r].name
      resource_group_lock_enabled     = false
      resource_group_creation_enabled = false
      mesh_peering_enabled            = true
      routing_address_space           = [local.address_spaces[r]]
      tags                            = local.network_tags
      hub_router_ip_address           = "1.2.3.4"
      #flow_timeout_in_minutes          = 4
      subnets = {
        # The module will currently fail attempting to attach a route table to AzureBastionSubnet
        AzureBastionSubnet = {
          address_prefixes             = [module.subnet_addressing[r].network_cidr_blocks["AzureBastionSubnet"]]
          assign_generated_route_table = false
        }
        ServiceNowVMs = {
          address_prefixes = [module.subnet_addressing[r].network_cidr_blocks["ServiceNowVM"]]
        }
      }
      # firewall = {
      #   sku_name              = "AZFW_VNet"
      #   sku_tier              = "Standard"
      #   threat_intel_mode     = "Off"
      #   subnet_address_prefix = module.subnet_addressing[r].network_cidr_blocks["AzureFirewallSubnet"]
      #   firewall_policy_id    = azurerm_firewall_policy.fwpolicy.id
      #   tags                  = local.firewall_tags
      # }
    }
  }
}
```

Want to wrap several paragraphs or other elements in a notice? Using Liquid to capture the content and then filter it with `markdownify` is a good way to go.

```html
{% raw %}{% capture notice-2 %}
#### New Site Features

* You can now have cover images on blog pages
* Drafts will now auto-save while writing
{% endcapture %}{% endraw %}

<div class="notice">{% raw %}{{ notice-2 | markdownify }}{% endraw %}</div>
```

{% capture notice-2 %}
#### New Site Features

* You can now have cover images on blog pages
* Drafts will now auto-save while writing
{% endcapture %}

<div class="notice">
  {{ notice-2 | markdownify }}
</div>

Or you could skip the capture and stick with straight HTML.

```html
<div class="notice">
  <h4>Message</h4>
  <p>A basic message.</p>
</div>
```

<div class="notice">
  <h4>Message</h4>
  <p>A basic message.</p>
</div>