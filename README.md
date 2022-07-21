# json2excel
前端json导出excel表格

//安装依赖
npm i -S file-saver
npm i -S xlsx
//引入组件
import toExcel from '@/excel/json2excel'
Vue.prototype.$toExcel = toExcel
//使用
data() {
    return {
      excelData: [
        {
          name: '张三',
          birthday: new Date('1990-01-01'),
          sex: '男',
          age: 28
        },
        {
          name: '李四',
          birthday: new Date('1991-01-01'),
          sex: '女',
          age: 27
        }
      ]
    }
  },
  methods: {
    downExcel() {
      const th = ['姓名', '生日', '性别', '年龄']
      const filterVal = ['name', 'birthday', 'sex', 'age']
      const data = this.excelData.map(v => filterVal.map(k => v[k]))
      const [fileName, fileType, sheetName] = ['测试下载', 'xlsx', '测试页']
      this.$toExcel({th, data, fileName, fileType, sheetName})
    }
  }
