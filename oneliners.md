# Oneliners

## Format a log saved as a single line
```bash
sed 's/[0-9]\{4\}-[0-9]\{2\}-[0-9]\{2\}/\n&/g' single_line.log > multi_line.log
```

Sed finds a date timestamp and prints it on a new line. It can format a log file that was saved as a single line and make it readable.



