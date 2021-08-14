# EXPLORE REAMDE

- This experimental branch, I was checking out the derive macro for Encodable and Decodable
- These derive macros can be applied to stratumv2 messages to serialize/deserialize correctly according to the specs

- I was running a test at: `/protocols/v2/binary-sv2/lib.rs:L58` to see how the derive macro will process the comments
above the struct

- I found that at `protocols/v2/no-serde-sv2/derive_codec/src/lib:remove_attributes()` will identify a `TokeTree::Punct` that contains the char `#`, this will indicate a doc comment, since they are interpreted as `#[doc_comment(...)]`

- `protocols/v2/no-serde-sv2/derive_codec/src/get_struct_properties()` will call `remove_attributes()` to remove comments before parsing the token stream
