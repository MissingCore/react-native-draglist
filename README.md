> [!IMPORTANT]
> For most of the documentation, refer to the [original `fivecar/react-native-draglist` repository](https://github.com/fivecar/react-native-draglist).

# Installation

To use this fork of `fivecar/react-native-draglist`, you need to add the following under the `dependencies` field in `package.json`:

```
"react-native-draglist": "github:MissingCore/react-native-draglist"
```

If you want to use a specific commit in this fork (ie: to prevent things accidentally breaking when we change things), you can add a commit hash such as:

```
"react-native-draglist": "github:MissingCore/react-native-draglist#6e926d101e6293785d5cab4c014ccdc4812c19d2"
```

> [!NOTE]  
> `@shopify/flash-list` should be an (optional?) peer dependency, meaning an error shouldn't be thrown if it's not installed (ie: if you only use the `<FlatList />` variant).

## Notable Commits

|                 Note                 |                                 DragList Version                                  |                                                                    Commit Hash                                                                     |
| :----------------------------------: | :-------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------: |
| Least Buggy Version w/ FlashList v1  |  [`v3.9.7`](https://github.com/fivecar/react-native-draglist/releases/tag/3.9.7)  | [`a3847ce4f9265853a12b865ba30902e907d43c20`](https://github.com/MissingCore/react-native-draglist/commit/a3847ce4f9265853a12b865ba30902e907d43c20) |
| Last Version Supporting FlashList v1 | [`v3.10.0`](https://github.com/fivecar/react-native-draglist/releases/tag/3.10.0) | [`ef0b66675719a72c2096cf3438bb4aa7dacbf7a7`](https://github.com/MissingCore/react-native-draglist/commit/ef0b66675719a72c2096cf3438bb4aa7dacbf7a7) |

## Use

There's 2 main exports:

- `"react-native-draglist"` is for the original `<FlatList />` implementation.
- `"react-native-draglist/dist/FlashList"` is for our `<FlashList />` implementation.

# Differences

- For the `<FlashList />` implementation:
  - Removed the `CustomFlatList` prop.
  - Renamed `containerStyle` prop to `wrapperStyle`.
  - The `<View />` wrapping the `<FlashList />` by default has `flex: 1` applied.
- For all implementations:
  - `renderItem` function now provides an `isDragging` value.
  - Removed the `key` prop on the rendered items ([for performance reasons](https://shopify.github.io/flash-list/docs/fundamentals/performant-components#remove-key-prop)).
    - This means you need to handle the [side effects of recycling](https://shopify.github.io/flash-list/docs/recycling).
