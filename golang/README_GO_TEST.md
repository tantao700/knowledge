# go test

### Test function

```go
func goPathEnv() (string, bool) {
	return "cpp", true
}
```

### Unit test function

```go
func Test_goPathEnv(t *testing.T) {
	tests := []struct {
		country   string
		expected1 string
		expected2 bool
	}{
		// TODO: Add test cases.
		{"zh", "cpp", true},
		{"us", "cpp", true},
		{"jp", "cpp", true},
		{"au", "cpp", true},
		{"au2", "cpp", true},
	}
	for _, tt := range tests {
        // different profile 
		if tt.country != "zh" {
			t.Run(tt.country, func(t *testing.T) {
				got, got1 := goPathEnv()
				if got != tt.expected1 && got1 == tt.expected2 {
					t.Errorf("goPathEnv() got = %v,%v, want %v,%v", got, got1, tt.expected1, tt.expected2)
				}
			})
		}
	}
}
```