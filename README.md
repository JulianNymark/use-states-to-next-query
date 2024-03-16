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
