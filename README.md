Этот документ в процессе написания Maksim.Sysoev@evraz.com

[[_TOC_]]
# Руководство по стилю Java

### 1. Рекомендации по форматированию

  - в качестве базовой единицы отступа следует использовать табуляцию (1 таб)

  - длина строки 120 символов

  - #### Отступы.

    Каждый раз, когда открывается новый блок или блочная конструкция,
    происходит смещение вправо на 1 таб относительно уровня

    ```
    public String reverseString(char[] s) {  
        for (int i = 0; i < (s.length / 2); i++) {
            char temp = s[i];
            s[i] = s[s.length - 1 - i];
            s[s.length - 1 - i] = temp;
        }
  
        //- после блока(for) смещение строк на уровень метода
        logger.info("строка развёрнута");
    
        return String.valueOf(s);
    }
    ```

  - #### Переносы.

    Если параметры метода или выражение не помещаются в одну строку, необходимо разбить на части по следующим правилам:
    - разбить после запятой
    - разбить до оператора
    
    ```
    private void calcObjectCounters(Account account, ContentVersion contentVersion,
        Attachment attachment) {
      
        //some code...
      
        //- оператор с выражением переносится на следующую строку с отступом.
        int calculatingResults = account.getResult() + contentVersion.getResult()
            + attachment.getResult();
    }
    ```
    
    если метод имеет слишком длинное название (больше 120 символов), тогда перенос только параметров метода

    ```
    private List<ObjectInfo> getObjectInfosSortedByFirstSnapshotCountsDesc(
        List<ObjectInfo> objectInfos) {
    
        //some code...
    
    }
    ```

  - #### Пустые строки.

      использование в следующих случаях:
      - между описаниями методов
      - между блочным/однострочным комментарием, логическими секциями внутри метода
  
      ```
      //- между описанием методов
      private void configSfObjects() {
          //code...
      }

      private void configPgObjects() {
          //code...
      }

      /**
      * Javadoc
      * @param counters параметр
      */
      private void addCalculators(CountersCalculator counters) {
          if (counters.getResult() <= 0) {
              return;
          }
      
          //- комментарий...
          calculators.add(counters);
      }
      ```

# Список необходимых для работы файлов

- [codestyle.xml](files/codestyle.xml)
