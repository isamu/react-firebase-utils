
### Usage

firestore tools

```js
const someDataOption = {
  queryFilter: (query) => {
    return query.orderBy("updateAt", "desc");
  },
  responseFilter: (data) => {
    const newData = {
      id: data.id,
      name: data.name,
      updateAt: moment.unix(data.updateAt.seconds).format("YYYY-MM-DD HH:mm:ss"),
      key: data.key
    };
    return newData;
  }
};

function App(props) {
  const { db, classes, user } = props;

  const [somedata, error] = useOnCollectionGroup(db, 'somedata', someDataOption)
  const [toys, error2] = useOnCollection(db, 'toys')

  return <div/>
}

```
