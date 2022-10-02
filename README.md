# React Native Android Bottomsheet (alpha)

## Why?

This library uses native Bottomsheet. Biggest wins are on accessibility. Styling can also be customised.

## Installation

```
yarn add react-native-android-bottomsheet
```

## API

### Simple usage

```jsx
import { BottomSheet } from 'react-native-android-bottomsheet';

<BottomSheet
  peekHeight={400}
  visible={visible}
  onDismiss={() => {
    setVisible(false);
  }}
>
  <View
    style={{
      flex: 1,
      backgroundColor: 'white',
    }}
  >
    <Text>Hello from bottomsheet</Text>
  </View>
</BottomSheet>;
```

- BottomSheet has no background by default. So, setting `backgroundColor` on view is important.

### BottomSheet with ScrollView

```jsx
import { ScrollView } from 'react-native';
import { BottomSheet } from 'react-native-android-bottomsheet';

<BottomSheet
  visible={visible}
  onDismiss={() => {
    setVisible(false);
  }}
>
  <ScrollView style={{ backgroundColor: 'white' }} nestedScrollEnabled>
    <Boxes />
  </ScrollView>
</BottomSheet>;
```

- For drag-to-close/expand gesture to work, make sure to add `nestedScrollEnabled` to the ScrollView

### BottomSheet with ScrollView and pull to refresh

```jsx
import { ScrollView, RefreshControl } from 'react-native';
import { BottomSheet } from 'react-native-android-bottomsheet';

<BottomSheet
  visible={visible}
  onDismiss={() => {
    setVisible(false);
  }}
>
  <ScrollView
    style={{ backgroundColor: 'white' }}
    refreshControl={
      <RefreshControl
        onRefresh={() => {
          setRefreshing(true);
          setTimeout(() => {
            setRefreshing(false);
          }, 2000);
        }}
        refreshing={refreshing}
      />
    }
  >
    <Boxes />
  </ScrollView>
</BottomSheet>;
```

## Props

```ts
type AndroidBottomsheetProps = {
  // To show/hide bottomsheet
  'visible': boolean;

  // gets called when bottomsheet is dismissed. Use this to reset visible state
  'onDismiss'?: () => void;

  // Collapsed bottomsheet height
  'peekHeight'?: number;

  // Expanded bottomsheet height
  'maxHeight'?: number;

  // Gets announced when bottomsheet is opened with TalkBack
  'aria-label'?: string;

  // To set backdrop dim ammount. Accepts value 0 to 1. 0 would make the backdrop transparent.
  'backdropDimAmount'?: number;

  // Determines whether bottomsheet can be cancelled by swiping or back button
  'cancelable'?: boolean;
};
```

## To run examples

- Clone the repo
- Go to example/
- yarn && yarn android
