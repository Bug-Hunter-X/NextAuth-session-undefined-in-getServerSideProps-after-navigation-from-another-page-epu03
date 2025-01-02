# NextAuth Session Undefined After Navigation

This repository demonstrates a bug where a NextAuth session is undefined in `getServerSideProps` when navigating to a page from another page that doesn't use `getServerSideProps`.  The session is correctly available when directly accessing the page.

## Bug Description

The `/about` page uses `getServerSideProps` to retrieve the user's session via NextAuth. When directly accessing `/about`, the session is properly fetched and displayed. However, when navigating to `/about` from `/` (which doesn't use `getServerSideProps`), the `session` object is `undefined`.

## Steps to Reproduce

1. Clone this repository.
2. Install dependencies: `npm install`
3. Run the development server: `npm run dev`
4. Navigate to `/`.  You'll see the link to the `/about` page.
5. Click the link to `/about`. You'll see that the session is undefined (or null).
6. Now, directly access `/about` in your browser.  You'll see the session is correctly loaded.

## Expected Behavior

The session should be available regardless of how the page is accessed.

## Actual Behavior

The session is only available when directly accessing `/about` in the browser.  When navigating from `/`, the session is undefined.

## Possible Cause

This might be related to how Next.js 15 handles caching and revalidation in combination with NextAuth's session management.