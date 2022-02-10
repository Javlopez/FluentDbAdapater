idea:
```go
//models.go
type Student struct {
 ID int
 SchoolID int
}

type School struct {
  ID int
  Name string
}
```


```go
//main.go
// Multiple Saves
f := NewFluent()
f.Insert(models.School{
  ID: 123,
  Name: "My School"
}).Insert(models.Student{}, use: [models.Student.ID])
```

