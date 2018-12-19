---
layout: "oci"
page_title: "Oracle Cloud Infrastructure: oci_dns_records"
sidebar_current: "docs-oci-datasource-dns-records"
description: |-
  Provides the list of Records in Oracle Cloud Infrastructure Dns service
---

# Data Source: oci_dns_records
This data source provides the list of Records in Oracle Cloud Infrastructure Dns service.

Gets all records in the specified zone. The results are
sorted by `domain` in alphabetical order by default. For more
information about records, see [Resource Record (RR) TYPEs](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-4).


## Example Usage

```hcl
data "oci_dns_records" "test_records" {
	#Required
	zone_name_or_id = "${oci_dns_zone_name_or.test_zone_name_or.id}"

	#Optional
	compartment_id = "${var.compartment_id}"
	domain = "${var.record_domain}"
	domain_contains = "${var.record_domain_contains}"
	rtype = "${var.record_rtype}"
	zone_version = "${var.record_zone_version}"
}
```

## Argument Reference

The following arguments are supported:

* `compartment_id` - (Optional) The OCID of the compartment the resource belongs to.
* `domain` - (Optional) Search by domain. Will match any record whose domain (case-insensitive) equals the provided value. 
* `domain_contains` - (Optional) Search by domain. Will match any record whose domain (case-insensitive) contains the provided value. 
* `rtype` - (Optional) Search by record type. Will match any record whose [type](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-4) (case-insensitive) equals the provided value. 
* `sort_by` - (Optional) The field by which to sort records. Allowed values are: domain|rtype|ttl
* `sort_order` - The order to sort the resources. Allowed values are: ASC|DESC 
* `zone_name_or_id` - (Required) The name or OCID of the target zone.
* `zone_version` - (Optional) The version of the zone for which data is requested. 


## Attributes Reference

The following attributes are exported:

* `records` - A collection of DNS resource records.

### DnsRecord Reference

The following attributes are exported:

* `compartment_id` - The OCID of the compartment the resource belongs to.
* `domain` - The fully qualified domain name where the record can be located. 
* `is_protected` - A Boolean flag indicating whether or not parts of the record are unable to be explicitly managed. 
* `rdata` - The record's data, as whitespace-delimited tokens in type-specific presentation format. All RDATA is normalized and the returned presentation of your RDATA may differ from its initial input. For more information about RDATA, see [Supported DNS Resource Record Types](https://docs.cloud.oracle.com/iaas/Content/DNS/Reference/supporteddnsresource.htm) 
* `record_hash` - A unique identifier for the record within its zone. 
* `rrset_version` - The latest version of the record's zone in which its RRSet differs from the preceding version. 
* `rtype` - The canonical name for the record's type, such as A or CNAME. For more information, see [Resource Record (RR) TYPEs](https://www.iana.org/assignments/dns-parameters/dns-parameters.xhtml#dns-parameters-4). 
* `ttl` - The Time To Live for the record, in seconds.
* `zone_name_or_id` - The name or OCID of the target zone.

