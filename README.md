re` entirely — throws `VMError` at construction (GHSA-m4wx-m65x-ghrr, supersedes GHSA-8hg8-63c5-gwmx). All of those shapes produce a NESTING_OVERRIDE-only resolver: the sandbox can `require('vm2')` but nothing else, which is a pure escape primitive with no legitimate use. To deny all requires, remove `nesting: true`. To allow nested VMs, provide an explicit `require` config so the trade-off is visible at the call site.

## Known Issues

-   It is not possible to define a class that extends a proxied class. This includes using a proxied class in `Object.create`.
-   Direct eval does not work.
-   Logging sandbox arrays will repeat the array part in the 
