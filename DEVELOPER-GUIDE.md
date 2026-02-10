# UK Energy Data for Developers

APIs and datasets for building energy-related applications.

## EPC API (Energy Performance Certificates)

Every EPC lodged in England and Wales since 2008.

```javascript
// Check if a property likely qualifies for ECO4
async function checkEco4Eligibility(postcode) {
  const res = await fetch(
    `https://epc.opendatacommunities.org/api/v1/domestic/search?postcode=${postcode}`,
    { headers: { Authorization: `Basic ${btoa(EPC_API_KEY + ':')}` } }
  );
  const data = await res.json();
  return data.rows.filter(r => ['E','F','G'].includes(r['current-energy-rating']));
}
```

- **URL:** https://epc.opendatacommunities.org/
- **Rate limit:** 5,000 requests/day
- **Format:** JSON, CSV

## Useful Links

- [Great British Energy Eligibility Checker](https://greatbritishenergy.com/eligibility-checker/) - Example of EPC data in a consumer app
- [Gov.uk ECO4](https://www.gov.uk/energy-company-obligation)
- [Ofgem Data Portal](https://www.ofgem.gov.uk/energy-data-and-research)
