<template>
  <div class="app-container">
    <el-row class="mb-4">
      <el-button>Default</el-button>
      <el-button type="primary">Primary</el-button>
      <el-button type="success">Success</el-button>
      <el-button type="info">Info</el-button>
      <el-button type="warning">Warning</el-button>
      <el-button type="danger">Danger</el-button>
      <el-button>中文</el-button>
    </el-row>
    <el-cascader v-model="value" :options="options" @change="handleChange" />

     <div>
      <el-checkbox v-model="checked1" label="Option 1" size="large" />
      <el-checkbox v-model="checked2" label="Option 2" size="large" />
      
  </div>
  时间<el-date-picker
        v-model="date"
        type="date"
        placeholder="Pick a day"
        :size="size"
      />
      <el-form :model="form" label-width="120px">
    <el-form-item label="Activity name">
      <el-input v-model="form.name" />
    </el-form-item>
    <el-form-item label="Activity zone">
      <el-select v-model="form.region" placeholder="please select your zone">
        <el-option label="Zone one" value="shanghai" />
        <el-option label="Zone two" value="beijing" />
      </el-select>
    </el-form-item>
    <el-form-item label="Activity time">
      <el-col :span="11">
        <el-date-picker
          v-model="form.date1"
          type="date"
          placeholder="Pick a date"
          style="width: 100%"
        />
      </el-col>
      <el-col :span="2" class="text-center">
        <span class="text-gray-500">-</span>
      </el-col>
      <el-col :span="11">
        <el-time-picker
          v-model="form.date2"
          placeholder="Pick a time"
          style="width: 100%"
        />
      </el-col>
    </el-form-item>
    <el-form-item label="Instant delivery">
      <el-switch v-model="form.delivery" />
    </el-form-item>
    <el-form-item label="Activity type">
      <el-checkbox-group v-model="form.type">
        <el-checkbox label="Online activities" name="type" />
        <el-checkbox label="Promotion activities" name="type" />
        <el-checkbox label="Offline activities" name="type" />
        <el-checkbox label="Simple brand exposure" name="type" />
      </el-checkbox-group>
    </el-form-item>
    <el-form-item label="Resources">
      <el-radio-group v-model="form.resource">
        <el-radio label="Sponsor" />
        <el-radio label="Venue" />
      </el-radio-group>
    </el-form-item>
    <el-form-item label="Activity form">
      <el-input v-model="form.desc" type="textarea" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="onSubmit">Create</el-button>
      <el-button>Cancel</el-button>
    </el-form-item>
  </el-form>
  <el-input v-model="input" placeholder="Please input" />
   <el-switch
    v-model="value"
    size="large"
    active-text="Open"
    inactive-text="Close"
  />
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="date" label="Date" width="180" />
    <el-table-column prop="name" label="Name" width="180" />
    <el-table-column prop="address" label="Address" />
  </el-table>

  <el-tag>Tag 1</el-tag>
  <el-tag class="ml-2" type="success">Tag 2</el-tag>
  <el-tag class="ml-2" type="info">Tag 3</el-tag>
  <el-tag class="ml-2" type="warning">Tag 4</el-tag>
  <el-tag class="ml-2" type="danger">Tag 5</el-tag>

  <el-button text @click="dialogVisible = true"
    >click to open the Dialog</el-button
  >

  <el-dialog
    v-model="dialogVisible"
    title="Tips"
    width="30%"
    :before-close="handleClose"
  >
    <span>This is a message</span>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogVisible = false">Cancel</el-button>
        <el-button type="primary" @click="dialogVisible = false"
          >Confirm</el-button
        >
      </span>
    </template>
  </el-dialog>

  <el-button :plain="true" @click="open2">success</el-button>
  <el-button :plain="true" @click="open3">warning</el-button>
  <el-button :plain="true" @click="open1">message</el-button>
  <el-button :plain="true" @click="open4">error</el-button>

  <el-popover
    placement="top-start"
    title="Title"
    :width="200"
    trigger="hover"
    content="this is content, this is content, this is content"
  >
    <template #reference>
      <el-button>Hover to activate</el-button>
    </template>
  </el-popover>

  <el-popover
    placement="bottom"
    title="Title"
    :width="200"
    trigger="click"
    content="this is content, this is content, this is content"
  >
    <template #reference>
      <el-button>Click to activate</el-button>
    </template>
  </el-popover>

  <el-popover
    ref="popover"
    placement="right"
    title="Title"
    :width="200"
    trigger="focus"
    content="this is content, this is content, this is content"
  >
    <template #reference>
      <el-button>Focus to activate</el-button>
    </template>
  </el-popover>

  <el-popover
    ref="popover"
    title="Title"
    :width="200"
    trigger="contextmenu"
    content="this is content, this is content, this is content"
  >
    <template #reference>
      <el-button>contextmenu to activate</el-button>
    </template>
  </el-popover>

  <el-popover
    v-model:visible="visible"
    placement="bottom"
    title="Title"
    :width="200"
    content="this is content, this is content, this is content"
  >
    <template #reference>
      <el-button @click="visible = !visible">Manual to activate</el-button>
    </template>
  </el-popover>
  <br>
  <el-divider />
  <el-divider />
  <el-divider />
  <el-divider />
  </div>

</template>

<script setup name="Dept">
import { ElMessage } from 'element-plus'
const handleChange = (value) => {
  console.log(value)
}
const onSubmit = () => {
  console.log('submit!')
}

const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
]
const open1 = () => {
  ElMessage('this is a message.')
}
const open2 = () => {
  ElMessage({
    message: 'Congrats, this is a success message.',
    type: 'success',
  })
}
const open3 = () => {
  ElMessage({
    message: 'Warning, this is a warning message.',
    type: 'warning',
  })
}
const open4 = () => {
  ElMessage.error('Oops, this is a error message.')
}

const dialogVisible = ref(false)

const handleClose = () => {
  ElMessageBox.confirm('Are you sure to close this dialog?')
    .then(() => {
      done()
    })
    .catch(() => {
      // catch error
    })
}
const size = ref<'' | 'large' | 'small'>('')
const input =ref('11')
const data = reactive({
  value: "",
  form:{},
  checked1:false,
  checked2:false,
  date:new Date(),
  options: [
    {
      value: "guide",
      label: "Guide",
      children: [
        {
          value: "disciplines",
          label: "Disciplines",
          children: [
            {
              value: "consistency",
              label: "Consistency",
            },
            {
              value: "feedback",
              label: "Feedback",
            },
            {
              value: "efficiency",
              label: "Efficiency",
            },
            {
              value: "controllability",
              label: "Controllability",
            },
          ],
        },
        {
          value: "navigation",
          label: "Navigation",
          children: [
            {
              value: "side nav",
              label: "Side Navigation",
            },
            {
              value: "top nav",
              label: "Top Navigation",
            },
          ],
        },
      ],
    },
    {
      value: "component",
      label: "Component",
      children: [
        {
          value: "basic",
          label: "Basic",
          children: [
            {
              value: "layout",
              label: "Layout",
            },
            {
              value: "color",
              label: "Color",
            },
            {
              value: "typography",
              label: "Typography",
            },
            {
              value: "icon",
              label: "Icon",
            },
            {
              value: "button",
              label: "Button",
            },
          ],
        },
        {
          value: "form",
          label: "Form",
          children: [
            {
              value: "radio",
              label: "Radio",
            },
            {
              value: "checkbox",
              label: "Checkbox",
            },
            {
              value: "input",
              label: "Input",
            },
            {
              value: "input-number",
              label: "InputNumber",
            },
            {
              value: "select",
              label: "Select",
            },
            {
              value: "cascader",
              label: "Cascader",
            },
            {
              value: "switch",
              label: "Switch",
            },
            {
              value: "slider",
              label: "Slider",
            },
            {
              value: "time-picker",
              label: "TimePicker",
            },
            {
              value: "date-picker",
              label: "DatePicker",
            },
            {
              value: "datetime-picker",
              label: "DateTimePicker",
            },
            {
              value: "upload",
              label: "Upload",
            },
            {
              value: "rate",
              label: "Rate",
            },
            {
              value: "form",
              label: "Form",
            },
          ],
        },
        {
          value: "data",
          label: "Data",
          children: [
            {
              value: "table",
              label: "Table",
            },
            {
              value: "tag",
              label: "Tag",
            },
            {
              value: "progress",
              label: "Progress",
            },
            {
              value: "tree",
              label: "Tree",
            },
            {
              value: "pagination",
              label: "Pagination",
            },
            {
              value: "badge",
              label: "Badge",
            },
          ],
        },
        {
          value: "notice",
          label: "Notice",
          children: [
            {
              value: "alert",
              label: "Alert",
            },
            {
              value: "loading",
              label: "Loading",
            },
            {
              value: "message",
              label: "Message",
            },
            {
              value: "message-box",
              label: "MessageBox",
            },
            {
              value: "notification",
              label: "Notification",
            },
          ],
        },
        {
          value: "navigation",
          label: "Navigation",
          children: [
            {
              value: "menu",
              label: "Menu",
            },
            {
              value: "tabs",
              label: "Tabs",
            },
            {
              value: "breadcrumb",
              label: "Breadcrumb",
            },
            {
              value: "dropdown",
              label: "Dropdown",
            },
            {
              value: "steps",
              label: "Steps",
            },
          ],
        },
        {
          value: "others",
          label: "Others",
          children: [
            {
              value: "dialog",
              label: "Dialog",
            },
            {
              value: "tooltip",
              label: "Tooltip",
            },
            {
              value: "popover",
              label: "Popover",
            },
            {
              value: "card",
              label: "Card",
            },
            {
              value: "carousel",
              label: "Carousel",
            },
            {
              value: "collapse",
              label: "Collapse",
            },
          ],
        },
      ],
    },
    {
      value: "resource",
      label: "Resource",
      children: [
        {
          value: "axure",
          label: "Axure Components",
        },
        {
          value: "sketch",
          label: "Sketch Templates",
        },
        {
          value: "docs",
          label: "Design Documentation",
        },
      ],
    },
  ],
});
const { value,form, checked1,checked2,date,options,} = toRefs(data);
</script>
