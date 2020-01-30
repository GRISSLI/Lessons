# Нужно реализовать поиск по предоставленным данным  
  
Результаты поиска выводятся по мере ввода   
При вводе менее трех букв выводим предупреждение о том что необходимо более 3х букв для поиска  
На поле ввода накладывается маска вида /^[A-я]+\s[A-я]+$/gm всё что выпадает за пределы формата не должно вводится  
  
В качестве исходных данных предоставляет кусок работающего кода 
<details>
  <summary>
    Посмотреть код
  </summary>

  ```js
import russian_names from '@/data/russian_names.json'
import russian_surnames from '@/data/russian_surnames.json'

export default {
  data: () => ({
    loading: true
  }),
  methods: {
    getDataNamesFromAPI(query) {
      return new Promise((resolve, reject) => {
        const items = this.dataNamesFromDB().find((e) => e.Name === query)
        setTimeout(() => {
          this.loading = false
          resolve({
            items
          })
        }, 1000)
      })
    },
    getDataSureNamesFromAPI(query) {
      return new Promise((resolve, reject) => {
        const items = this.dataSurenamesFromDB().find(
          (e) => e.Surname === query
        )
        setTimeout(() => {
          this.loading = false
          resolve({
            items
          })
        }, 1000)
      })
    },
    dataNamesFromDB() {
      return russian_names
    },
    dataSurenamesFromDB() {
      return russian_surnames
    }
  }
}
  ```
</details>


данные для импорта в этот код можно скачать здесь: [Download](https://github.com/GRISSLI/Lessons/raw/master/JSON.zip)
(который нужно оставить без изменений и использовать в своем проекте для получения данных)  
  
У поля поиска существуют модификаторы в виде чекбоксов  
Они могут применятся параллельно на результате  
В поле ввода вводится текст в формате "имя фамилия"  
При вводе только имени, в результатах указывается "имя ..."  
При имени и фамилии выводится результат в виде "имя фамилия"  
  
Описание модификаторов:  
Uppercase - преобразование в верхний регистр  
Lowercase - преобразование в нижний регистр  
Translite - транслит в англ буквы  
Reverse - результат должен быть выведен задом-наперед  


  
Пример:  
![Test](https://i.postimg.cc/KvRk1xSd/unknown.png)
