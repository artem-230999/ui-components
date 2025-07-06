
1. Input с типом File нельзя стилизовать, потому что добраться к ним нет возможности.
  Можно его скрыть и сделать по своему. Пример:
  <label class="file-upload">
    <input type="file" id="file" name="file" class="file-upload__input">
    <span class="file-upload__button">Выбрать файл</span>
    <span class="file-upload__label">Файл не выбран</span>
  </label>

2. Скрытие базового input и стилизация нового
  .file-upload {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  position: relative;
  cursor: pointer;
}
.file-upload__input {
  position: absolute;
  opacity: 0;
}
.file-upload__button {
  padding: 5px 10px;
  border-radius: 4px;
  font-weight: 700;
  color: #fff;
  background-color: #007bff;
  cursor: pointer;
  position: relative;
  z-index: 2;
}
.file-upload__label {
  font-size: 20px;
  color: #555;
}

3. JS для изменения названия файла. Берет название файла, проверяет что там что-то написано и подставляет имя файла.
 const input = document.querySelector('.file-upload__input')
    const label = document.querySelector('.file-upload__label')

    input.addEventListener('change', () => {
      console.log(input.files);
      const a = [...input.files].map(f => f.name);
      console.log(a);
      

      label.textContent = input.files.length > 0 ? a.join(',') : "Файл не выбран";
    });

