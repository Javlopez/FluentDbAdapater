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


```go
//main.go
// Multiple Saves with commit will return error if the commit is not success
f := NewFluentTransaction()
f.Insert(models.School{
  ID: 123,
  Name: "My School"
}).Insert(models.Student{}, use: [models.Student.ID]).Commit()

// Multiple Saves with commit and default logger it it fails
logger := log.New()
f := NewFluentTransaction()
f.Insert(models.School{
  ID: 123,
  Name: "My School"
}).Insert(models.Student{}, use: [models.Student.ID]).Commit().OrFail(logger)



//Query
f := NewFluent()
f.Select("name", "id").From(models.School).Scan(models.School) 

f.Select("name", "id").From(models.School).RowScan(models.School)

```


