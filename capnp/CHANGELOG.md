## v0.9.3
- Add IntoInternalStructReader trait and struct_list::Builder::set_with_caveats() method.
- Update deprecation attributes, to satisfy clippy.

## v0.9.2
- Rename a bunch of as_reader() methods to into_reader(), to satisfy clippy.

## v0.9.1
- Avoid some unnecessary heap allocation that could occur when reading multisegment messages.

## v0.9.0
- Add message::Builder::set_root_canonical() method. Relies on a new signature for SetPointerBuilder.
- Mark bytes_to_words() and bytes_to_words_mut() as unsafe, due to possible alignment issues. Please
  refer to https://github.com/capnproto/capnproto-rust/issues/101 for discussion.
- Delete deprecated items.
- Drop support for automatically imbuing message builders with capabilities (was unsafe). You should
  use capnp_rpc::ImbuedMessageBuilder now if you want that functionality. See the calculator example.
- Bump minimum supported rustc version to 1.26.0.

## v0.8.17
- Deprecate borrow() in favor of reborrow().

## v0.8.16
- Add serialize::write_message_segments().
- Fix bug where is_canonical() could sometimes erroneously return true.

## v0.8.15
- Add message::Builder::into_reader() and message::Reader::into_typed().

## v0.8.14
- Add message::TypedReader.
- Appease new "tyvar_behind_raw_pointer" lint (see https://github.com/rust-lang/rust/issues/46906).

## v0.8.13
- Implement capability_list, to support List(Interface).

## v0.8.12
- Avoid constructing (zero-length) slices from null pointers, as it seems to be a possible
  source of undefined behavior.
- Add some IntoIterator implementations.

## v0.8.11
- Avoid some situations where we would construct (but not dereference) out-of-bounds pointers.

## v0.8.10
- Deprecate Word::from() in favor of capnp_word!().
- Add constant::Reader to support struct and list constants.

## v0.8.9
- In canonicalization, account the possibility of nonzero padding in primitive lists.
- Do bounds-checking by (ptr, size) pairs rather than (ptr, end_ptr) pairs.

## v0.8.8
- Fix some canonicalization bugs.

## v0.8.7
- Implement `as_reader()` for lists.
- Implement `canonicalize()` and `is_canonical()`.
- Fix bug where `total_size()` returned wrong answer on empty struct lists.

## v0.8.6
- Implement struct list upgrades.
- Fix bug where `message.init_root::<any_pointer::Builder>()` did not clear the old value.

## v0.8.5
- Eliminate possible void-list-amplification in total_size().

## v0.8.4
- Eliminate panics in total_size() and set_root().
- Eliminate possible void-list-amplification in zero_object_helper().

## v0.8.3
- Prevent integer overflow possible with very long struct lists on 32-bit systems.
- Fix bug where the capnp_word!() macro was not exported for big endian targets.

## v0.8.2
- Shave some bytes off the representation of StructReader and friends.
- Fix some potential integer overflows.

## v0.8.1
- Redesign segment arenas to require less unsafe code.

## v0.8.0
- Replace optional GJ dependency with futures-rs.
- Remove `ResultsDoneHook` hack.
- No breaking changes for non-RPC users.

## v0.7.5
- Implement DoubleEndedIter for ListIter.
- Implement From<std::str::Utf8Error> for ::capnp::Error.
- Address some new linter warnings.

## v0.7.4
- Fix rare case where `serialize_packed::read()` could fail on valid input.

### v0.7.3
- Get `message::Builder::get_root_as_reader()` to work on empty messages.

### v0.7.2
- Implement `From<std::string::FromUtf8Error>` for `capnp::Error`
- More and better iterators.
