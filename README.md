## Snapshot testing

> Snapshot tests are a very useful tool whenever you want to make sure your UI does not change
> unexpectedly.
>
> A typical snapshot test case renders a UI component, takes a snapshot, then compares it to a
> reference snapshot file stored alongside the test. The test will fail if the two snapshots do
> not match: either the change is unexpected, or the reference snapshot needs to be updated to the
> new version of the UI component.

Source: [jestjs.io](https://jestjs.io/docs/snapshot-testing)

Came across this in a `viem` test using `toMatchInlineSnapshot()`.

```ts
test("gasPrice", async () => {
    expect(
        await signTransaction(walletClient, {
            account: privateKeyToAccount(sourceAccount.privateKey),
            ...baseLegacy,
            gasPrice: parseGwei("20"),
        })
    ).toMatchInlineSnapshot(
        '"0xf8518203118504a817c800825208808080259f672886c0db7d3a2710b5bb8b64fd516ff4fede94f34e76b22f451e5ff92ecfa0627283bbafb0600cd997c8dbfa6f4173c5376e2c4c57967541e171fb110b6d64"'
    );
});
```

See comment in [code review](https://github.com/clabs-co/viem/pull/6#discussion_r1378906295).
