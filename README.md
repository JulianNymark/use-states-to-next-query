# You probably want `nuqs`

https://www.npmjs.com/package/nuqs is a much more polished & popular package that does the same thing (but better)! I couldn't initially find it before this package was created. One small difference I could see is that `nuqs` requires you to `use client` (and disable ssr by dynamically loading it or get hydration errors when linking a page with query params) whereas this package does everything within `useEffect` so it's forced to be _purely_ client-side. I'll keep this package in existence purely for its simplicity, but I highly recommend you use `nuqs` over this.

# Usage

Pass the return value from `React.useState()` into the `value` of a Record / dict. The `key` becomes the query parameter used. the router passed in is a Nextjs Pages router.

```tsx
const router = useRouter();

const search = useState("");
const chips = useState<string[]>([]);

const [currentSearch, setSearch] = search;
const [currentChips, setChips] = chips;

useStatesToNextQuery(router, {
  search,
  chips,
});

setSearch('testinput')
setChips(['testinput1', 'testinput2'])
```
In the example above, the resulting query params will be the following:

`?search=testinput&chips=testinput1&chips=testinput2`

Any changes you make to the states will now update in the URL.
