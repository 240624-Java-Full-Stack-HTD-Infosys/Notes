# Setting up Redux

### 1. Install Dependencies

First, install Redux, React Redux, Redux Toolkit, and TypeScript types:

```bash
npm install redux react-redux @reduxjs/toolkit
npm install @types/react-redux
```

### 2. Create the Redux Store

#### a. Define the State Types

Define the structure of your user state:

```typescript
// src/store/types.ts
export interface User {
  id: number;
  name: string;
  email: string;
}

export interface UserState {
  users: User[];
  loading: boolean;
  error: string | null;
}
```

#### b. Create Reducers

Reducers specify how the application's state changes in response to actions.

```typescript
// src/store/reducers/userReducer.ts
import { createSlice, PayloadAction } from '@reduxjs/toolkit';
import { UserState, User } from '../types';

const initialState: UserState = {
  users: [],
  loading: false,
  error: null,
};

const userSlice = createSlice({
  name: 'users',
  initialState,
  reducers: {
    fetchUsersStart(state) {
      state.loading = true;
      state.error = null;
    },
    fetchUsersSuccess(state, action: PayloadAction<User[]>) {
      state.users = action.payload;
      state.loading = false;
    },
    fetchUsersFailure(state, action: PayloadAction<string>) {
      state.error = action.payload;
      state.loading = false;
    },
  },
});

export const { fetchUsersStart, fetchUsersSuccess, fetchUsersFailure } = userSlice.actions;
export default userSlice.reducer;
```

In this example, `createSlice` helps manage the user state by automatically generating action creators and action types.

#### c. Configure the Store

Set up the store with the reducer:

```typescript
// src/store/store.ts
import { configureStore } from '@reduxjs/toolkit';
import userReducer from './reducers/userReducer';

export const store = configureStore({
  reducer: {
    users: userReducer,
  },
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

### 3. Provide the Store to the React Application

Wrap your application with the `Provider` component to make the store accessible:

```typescript
// src/index.tsx
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import { store } from './store/store';
import App from './App';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

### 4. Use Redux State and Actions in Components

#### a. Define Typed Hooks

For type safety, define typed versions of `useSelector` and `useDispatch`:

```typescript
// src/store/hooks.ts
import { TypedUseSelectorHook, useDispatch, useSelector } from 'react-redux';
import type { RootState, AppDispatch } from './store';

export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;
```

#### b. Fetch and Display Users

Create a component to fetch and display the list of users:

```typescript
// src/components/UserList.tsx
import React, { useEffect } from 'react';
import { useAppDispatch, useAppSelector } from '../store/hooks';
import { fetchUsersStart, fetchUsersSuccess, fetchUsersFailure } from '../store/reducers/userReducer';
import { User } from '../store/types';

const fetchUsers = async (dispatch: ReturnType<typeof useAppDispatch>) => {
  dispatch(fetchUsersStart());
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    const data: User[] = await response.json();
    dispatch(fetchUsersSuccess(data));
  } catch (error) {
    dispatch(fetchUsersFailure(error.toString()));
  }
};

const UserList: React.FC = () => {
  const dispatch = useAppDispatch();
  const { users, loading, error } = useAppSelector((state) => state.users);

  useEffect(() => {
    fetchUsers(dispatch);
  }, [dispatch]);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>
          {user.name} - {user.email}
        </li>
      ))}
    </ul>
  );
};

export default UserList;
```

**Explanation:**
- The `UserList` component fetches the list of users from an API.
- The `useEffect` hook dispatches the fetch actions when the component mounts.
- The `fetchUsers` function fetches user data and dispatches appropriate actions based on the result.
- The component displays a loading message, error message, or the list of users based on the current state.

