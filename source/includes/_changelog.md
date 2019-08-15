# Changelog

**August 15, 2019**

* [BETA] Improved structure of the `autoEmailStatus` field

**August 14, 2019**

* A new version of `getRegistrantsByBrokerage` (V2) is now available on the production endpoint, more details [here](https://spac.io/docs/api/#brokerage-leads-v2)

**August 13, 2019**

* `getOHSessions` is now available on the beta endpoint
* [BETA] Added the `autoEmailStatus` field
* Added the `note` field

**June 12, 2019**

* `getRegistrantsByTeam` is now available on the beta endpoint

**June 10, 2019**

* [BETA] Pagination has been introduced for `getRegistrantsByBrokerage`, more details [here](https://spac.io/docs/api/#beta-brokerage-leads)

**June 4, 2019**

* `getRegistrantsByBrokerage` is now available on the production endpoint

**May 30, 2019**

* [BETA] Leads from `getRegistrantsByBrokerage` should no longer include ones belonging to "sample" properties

**May 10, 2019**

* [BETA] Added `plid` (provider listing ID) field to return from `getRegistrantsByBrokerage` - this can be a platform specific ID or property MLS ID

<aside class="notice">
The property MLS ID can vary if it's listed in multiple regions
</aside>

**May 1, 2019**

* [BETA] Improved the structure of `answersObj` field 
* [BETA] Added the agent associated with lead under `agentEmail`