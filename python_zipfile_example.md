#python #zip #zipfile
```python
import io
import typing as t
import zipfile

archive_buffer = io.BytesIO()
archive = zipfile.ZipFile(file=archive_buffer, mode='w')

inner_file_content: t.Union[str, bytes] = ...

archive.writestr('inner_file_name.ext', inner_file_content)
```

#django #http #response
```python
response = HttpResponse(
	content=archive_buffer.getvalue(),
	status=200,
	content_type='application/zip',
)
response['Content-Disposition'] = 'attachment; filename=archive-name.zip'
```