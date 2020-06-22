<template>
  <section class="main">
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item><i class="el-icon-rank"></i> 我的客户</el-breadcrumb-item>
        <el-breadcrumb-item>客户列表</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="container">
      <div class="plugins-tips">
        我的客户列表
      </div>
      <div class="drag-box">
        <div class="drag-box-item">
          <div class="item-title">基金类</div>
          <draggable v-model="todo"
                     @remove="removeHandle"
                     :options="dragOptions">
            <transition-group tag="div"
                              id="todo"
                              class="item-ul">
              <div v-for="item in todo"
                   class="drag-list"
                   :key="item.id">
                {{item.content}}
                <div>
                  <i class="el-icon-lx-mobilefill">{{item.tel}}</i>
                </div>
              </div>
            </transition-group>
          </draggable>
        </div>
        <div class="drag-box-item">
          <div class="item-title">证券类</div>
          <draggable v-model="doing"
                     @remove="removeHandle"
                     :options="dragOptions">
            <transition-group tag="div"
                              id="doing"
                              class="item-ul">
              <div v-for="item in doing"
                   class="drag-list"
                   :key="item.id">
                {{item.content}}
              </div>
            </transition-group>
          </draggable>
        </div>
        <div class="drag-box-item">
          <div class="item-title">现金管理类</div>
          <draggable v-model="done"
                     @remove="removeHandle"
                     :options="dragOptions">
            <transition-group tag="div"
                              id="done"
                              class="item-ul">
              <div v-for="item in done"
                   class="drag-list"
                   :key="item.id">
                {{item.content}}
              </div>
            </transition-group>
          </draggable>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import draggable from 'vuedraggable'
export default {
  name: 'draglist',
  data() {
    return {
      dragOptions: {
        animation: 120,
        scroll: true,
        group: 'sortlist',
        ghostClass: 'ghost-style'
      },
      todo: [
        {
          id: 1,
          content: '朱丹丹',
          tel: '15623452536'
        },
        {
          id: 2,
          content: '宋宇航',
          tel: '15623452536'
        },
        {
          id: 3,
          content: '张迪',
          tel: '15623452536'
        }
      ],
      doing: [
        {
          id: 1,
          content: '开发登录注册页面'
        },
        {
          id: 2,
          content: '开发头部组件'
        },
        {
          id: 3,
          content: '开发表格相关组件'
        },
        {
          id: 4,
          content: '开发表单相关组件'
        }
      ],
      done: [
        {
          id: 1,
          content: '初始化项目，生成工程目录，完成相关配置'
        },
        {
          id: 2,
          content: '开发项目整体框架'
        }
      ]
    }
  },
  components: {
    draggable
  },
  methods: {
    removeHandle(event) {
      console.log(event);
      this.$message.success(`从 ${event.from.id} 移动到 ${event.to.id} `);
    }
  }
}

</script>

<style scoped>
.drag-box {
    display: flex;
    user-select: none;
}
.drag-box-item {
    flex: 1;
    max-width: 330px;
    min-width: 300px;
    background-color: #eff1f5;
    margin-right: 16px;
    border-radius: 6px;
    border: 1px #e1e4e8 solid;
}
.item-title {
    padding: 8px 8px 8px 12px;
    font-size: 14px;
    line-height: 1.5;
    color: #24292e;
    font-weight: 600;
}
.item-ul {
    padding: 0 8px 8px;
    height: 500px;
    overflow-y: scroll;
}
.item-ul::-webkit-scrollbar {
    width: 0;
}
.drag-list {
    border: 1px #e1e4e8 solid;
    padding: 10px;
    margin: 5px 0 10px;
    list-style: none;
    background-color: #fff;
    border-radius: 6px;
    cursor: pointer;
    -webkit-transition: border 0.3s ease-in;
    transition: border 0.3s ease-in;
}
.drag-list:hover {
    border: 1px solid #20a0ff;
}
.drag-title {
    font-weight: 400;
    line-height: 25px;
    margin: 10px 0;
    font-size: 22px;
    color: #1f2f3d;
}
.ghost-style {
    display: block;
    color: transparent;
    border-style: dashed;
}
</style>
