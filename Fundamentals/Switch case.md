`switch-case` statements are so useful in filtering what kind of logic you want to apply to different cases.

### Example
- from [[React]]

Here’s an example where we are returning a different React component for each `case` value.
```javascript
const [active, setActive] = useState<string>('Intro');

const pages = (active: string) => {
    switch (active) {
      case "Intro":
        return <Intro setActiveComponent={setActiveComponent} />;
      case "Gender":
        return (
          <Gender
            handleInput={handleInput}
            setActiveComponent={setActiveComponent}
          />
        );
      case "Info":
        return <Info result={result} />;
      default:
        redirect("/error");
        break;
    }
  };
```