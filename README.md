# rules_cc_embed_data

The `cc_embed_data` rule embeds `srcs` into a C++ module. It generates a header
file like:

```
namespace embed_data {
struct FileToc {
  const char* name;             // the file's original name
  const char* data;             // beginning of the file
  size_t size;                  // length of the file
};
}  // namespace embed_data
namespace foo {
extern const struct ::embed_data::FileToc* this_rule_name_create();
}
```

The `this_rule_name()` function will return an array of FileToc
structs terminated by one that has nullptr 'name' and 'data' fields.
The 'data' field always has an extra null terminator at the end (which
is not included in the size).

## Provenance

This was imported from [`iree-org/iree`](https://github.com/iree-org/iree) at
commit `7f4c2d27f17380bf6b1e3b2fe8619916f0d222e5` from the directory
`build_tools/embed_data`.

### Modifications

* Add `MODULE.bazel` for external dependencies
* Take dependency on googletest repository
* Move sources in to subdirectories.
* Change `iree` namespacing to `embed_data`
