---
title: "Multi-tenant"
date: 2018-03-14
layout: default
---

# Multi-Tenant Laravel - Tom Schlick
## Laracon US 2017

## Why?

* Multiple customers on one server
* Single deployment point
* Easier maintenance

# DB Structure

## Strategy: Single Database
* data from all tenants is help together
* tenant_id in each table
* add a where to all queries
#### Laravel Way
Add a TenantScope

```
class TenantScope implements Scope
{
    public function apply(Builder $builder, Model $model)
    {
        $builder->where('tenant_id',tenant()->id);
    }
}

```
And apply to models:
```
protected static function boot()
{
    parent::boot();

    static::addGlobalScope(new TenantScope);
}
```

### Pros
* very conventional, lots of knowledge
* migrations stay simple
* easy to display data from multiple tenants if you need to
### Cons
* must include scopes or WHERE - you will miss one!
* using third party packages may be difficult - adding the tenant_id
* hard to scale database
* painful to export data for customer

## Strategy Multiple Databases
* separate database per tenant
* each tenant has a full copy of the application in their own database including migrations

### How
* shared database as a router -> connects the current domain to the proper tenant database
* database then changes on the fly:
* two connections shared and tenant.

### Pro
* single point where data is segmented
* less chance of data being exposed to wrong customer
* third party packages can be used off the shelf
* easier long term scalability (horizontally)
* data portability - backups easier per db - easy to restore one customer which has messed something up.
* enterprise can transition to on-premise easily
* easy to delete one tenant's data
* customers can be clustered together
* deploy and maintain can be done gradually
* customers can choose their data physical location
* beta customers are possible

### Don
* more complex migrations
* two sets of migrations, shared and tenants


# Choosing Strategy
1. Do you commonly need to display information from multiple tenants on the same page?
2. Do you need the option to segment, export, or privately host data for particular customers?
3. Do you plan to use a lot of third party packages?
4. Is your customer's data highly sensitive?

# Segment all things
Queued Jobs
