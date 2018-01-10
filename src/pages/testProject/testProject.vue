<template>
  <div id="testProject">
    <div class="content">
        <headerGuide></headerGuide>
        <sidebar></sidebar>
        <!--main content start-->
        <section id="main-content">
            <section class="wrapper">
                <!--top-button start-->
                <div class="row">
                    <div class="col-lg-12 top-btn">
                        <a class="btn btn-white" data-toggle="modal" href="#insertModal"><i class="icon-plus"></i> 添加</a>
                        <a class="btn btn-white" data-toggle="modal" href="#deleteModal"><i class="icon-trash"></i> 删除</a>
                        <a class="btn btn-white" data-toggle="modal" href="#updateModal" @click="getSelected"><i class="icon-edit"></i> 修改</a>
                        <a class="btn btn-white"  @click="to"><i class="icon-cog"></i> 进入</a>
                        <!-- insertModal start -->
                        <div class="modal fade" id="insertModal" tabindex="-1" role="dialog" aria-labelledby="insertModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                                        <h4 class="modal-title">添加测试项目</h4>
                                    </div>
                                    <div class="modal-body">
                                        <!-- modal-body start -->
                                        <section class="panel">
                                            <form id="insertForm" class="form-horizontal" role="form">
                                                <div class="form-group">
                                                    <label class="col-lg-3 control-label">测试项目编号</label>
                                                    <div class="col-lg-5">
                                                        <input type="text" class="form-control" name="testProjectCode">
                                                    </div>
                                                </div>
                                                <div class="form-group">
                                                    <label class="col-lg-3 control-label">测试项目名称</label>
                                                    <div class="col-lg-5">
                                                        <input type="text" class="form-control" name="testProjectName">
                                                    </div>
                                                </div>
                                                <div class="form-group">
                                                    <label class="col-lg-3 control-label">描述</label>
                                                    <div class="col-lg-5">
                                                        <textarea class="form-control" rows="3" name="taskDescription"></textarea>
                                                    </div>
                                                </div>
                                            </form>
                                        </section>
                                        <!-- modal-body end -->
                                    </div>
                                    <div class="modal-footer">
                                        <button data-dismiss="modal" class="btn btn-default" type="button">取消</button>
                                        <button data-dismiss="modal" class="btn btn-success" type="button" v-on:click="insert()">添加</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- insertModal end -->
                        <!-- delModal start -->
                        <div class="modal fade" id="deleteModal" tabindex="-1" role="dialog" aria-labelledby="insertModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                                        <h4 class="modal-title">删除测试项目</h4>
                                    </div>
                                    <div class="modal-body">
                                        <!-- modal-body start -->
                                        <h4>确认删除测试项目？</h4>
                                        <!-- modal-body end -->
                                    </div>
                                    <div class="modal-footer">
                                        <button data-dismiss="modal" class="btn btn-default" type="button">取消</button>
                                        <button data-dismiss="modal" class="btn btn-success" type="button" v-on:click="del">删除</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- delModal end -->
                        <!-- updateModal start -->
                        <div class="modal fade" id="updateModal" tabindex="-1" role="dialog" aria-labelledby="updateModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                                        <h4 class="modal-title">修改测试项目</h4>
                                    </div>
                                    <div class="modal-body">
                                        <!-- modal-body start -->
                                        <section class="panel">
                                            <form id="updateForm" class="form-horizontal" role="form">
                                                <div class="form-group hidden">
                                                    <label class="col-lg-3 control-label">测试项目编号</label>
                                                    <div class="col-lg-5">
                                                        <input type="text" class="form-control" name="id" :value="selectedId">
                                                    </div>
                                                </div>
                                                <div class="form-group">
                                                    <label class="col-lg-3 control-label">测试项目编号</label>
                                                    <div class="col-lg-5">
                                                        <input type="text" class="form-control" name="testProjectCode">
                                                    </div>
                                                </div>
                                                <div class="form-group">
                                                    <label class="col-lg-3 control-label">测试项目名称</label>
                                                    <div class="col-lg-5">
                                                        <input type="text" class="form-control" name="testProjectName">
                                                    </div>
                                                </div>
                                                <div class="form-group">
                                                    <label class="col-lg-3 control-label">描述</label>
                                                    <div class="col-lg-5">
                                                        <textarea class="form-control" rows="3" name="taskDescription"></textarea>
                                                    </div>
                                                </div>
                                            </form>
                                        </section>
                                        <!-- modal-body end -->
                                    </div>
                                    <div class="modal-footer">
                                        <button data-dismiss="modal" class="btn btn-default" type="button">取消</button>
                                        <button data-dismiss="modal" class="btn btn-success" type="button" v-on:click="update">修改</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- updateModal end -->
                        <!-- successModal start -->
                        <div class="modal fade" id="successModal" tabindex="-1" role="dialog" aria-labelledby="successModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                                        <h4 class="modal-title">操作成功</h4>
                                    </div>
                                    <div class="modal-body">
                                        <h4>操作成功！</h4>
                                    </div>
                                    <div class="modal-footer">
                                        <button data-dismiss="modal" class="btn btn-success" type="button">确定</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- successModal end -->
                        <!-- failModal start -->
                        <div class="modal fade" id="failModal" tabindex="-1" role="dialog" aria-labelledby="failModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                                        <h4 class="modal-title">操作失败</h4>
                                    </div>
                                    <div class="modal-body">
                                        <h4>操作失败！</h4>
                                    </div>
                                    <div class="modal-footer">
                                        <button data-dismiss="modal" class="btn btn-success" type="button">确定</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- failModal end -->
                        <!-- selectAlertModal start -->
                        <div class="modal fade" id="selectAlertModal" tabindex="-1" role="dialog" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
                                        <h4 class="modal-title">操作失败</h4>
                                    </div>
                                    <div class="modal-body">
                                        <h4>请先选中一条数据！</h4>
                                    </div>
                                    <div class="modal-footer">
                                        <button data-dismiss="modal" class="btn btn-success" type="button">确定</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- selectAlertModal end -->
                    </div>
                </div>
                <!--topbutton end-->
                <!-- table start -->
                <div class="row">
                    <div class="col-lg-12">
                        <section class="panel">
                            <header class="panel-heading">
                                测试项目管理
                            </header>
                            <div class="filter">
                                <div class="row">
                                    <form class="form-horizontal col-lg-12">
                                        <div class="form-group">
                                            <label class="col-lg-1 control-label">搜索</label>
                                            <div class="col-lg-2">
                                                <input type="text" class="form-control" placeholder="请输入项目编号" name="" v-model="queryKey">
                                            </div>
                                            <div class="col-lg-1">
                                                <a class="btn btn-white" @click="queryTestProject()">搜索</a>
                                            </div>
                                            <label class="col-sm-4 col-lg-offset-1 control-label">展示条目</label>
                                            <div class="col-sm-2">
                                                <select size="1" name="sample_1_length" aria-controls="sample_1" class="form-control" v-model="pageSize" id="mySelect">
                                                    <option value="5" selected>5</option>
                                                    <option value="10">10</option>
                                                    <option value="20">20</option>
                                                    <option value="50">50</option>
                                                </select>
                                            </div>
                                            <div class="col-lg-1"><a class="btn btn-white" @click="getTestProject(1, {pageSize}, 'id', 'asc')">刷新</a></div>
                                        </div>
                                    </form>
                                </div>
                            </div>
                            <!-- 表格 -->
                            <table class="table table-striped table-bordered border-top text-center" id="">
                                <thead>
                                    <tr>
                                        <th width="5%" class="text-center">
                                            <!-- <input type="checkbox" v-model="checked"  name="chk_all" id="chk_all" /> -->
                                        </th>
                                        <th class="hidden-phone text-center" data-order="id" data-sort="asc" onclick="resort(this)">编号 <span class="icon-sort-up" aria-hidden="true"></span></th>
                                        <th class="text-center">名称</th>
                                        <th class="hidden-phone text-center">描述</th>
                                        <th class="hidden">caselibId</th>
                                    </tr>
                                </thead>
                                <tbody id="testProjectTable">
                                    <tr class="odd gradeX" v-for="project in testProjectList" :id="project.id">
                                        <td width="5%">
                                            <input type="radio" name="chk_list" :id="project.id" />
                                        </td>
                                        <td class="center hidden-phone" width="20%">{{ project.testProjectCode }}</td>
                                        <td width="20%">{{ project.testProjectName }}</td>
                                        <td class="hidden-phone" width="40%">{{ project.taskDescription }}</td>
                                        <td class="hidden">{{project.caselibId}}</td>
                                    </tr>
                                </tbody>
                            </table>
                            <!-- 分页 -->
                            <div class="row">
                                <div class="col-lg-12 text-center">
                                    <div class="pagination-wrap" v-if="totalPage!=0">
                                        <ul class="pagination">
                                            <li :class="currentPage==1?'disabled':''"><a href="javascript:;" @click="turnToPage(1)">首页</a></li>
                                            <li :class="currentPage==1?'disabled':''"><a @click="turnToPage(currentPage-1)" href="javascript:;">上一页</a></li>
                                            <li>
                                                <a href="javascript:;" @click="turnToPage(currentPage-3)" v-text="currentPage-3" v-if="currentPage-3>0"></a>
                                            </li>
                                            <li>
                                                <a href="javascript:;" @click="turnToPage(currentPage-2)" v-text="currentPage-2" v-if="currentPage-2>0"></a>
                                            </li>
                                            <li>
                                                <a href="javascript:;" @click="turnToPage(currentPage-1)" v-text="currentPage-1" v-if="currentPage-1>0"></a>
                                            </li>
                                            <li class="active"><a href="javascript:;" @click="turnToPage(currentPage)" v-text="currentPage"></a></li>
                                            <li>
                                                <a href="javascript:;" @click="turnToPage(currentPage+1)" v-text="currentPage+1" v-if="currentPage+1<=totalPage"></a>
                                            </li>
                                            <li>
                                                <a href="javascript:;" @click="turnToPage(currentPage+2)" v-text="currentPage+2" v-if="currentPage+2<=totalPage"></a>
                                            </li>
                                            <li>
                                                <a href="javascript:;" @click="turnToPage(currentPage+3)" v-text="currentPage+3" v-if="currentPage+3<=totalPage"></a>
                                            </li>
                                            <li :class="currentPage==totalPage?'disabled':''"><a href="javascript:;" @click="turnToPage(currentPage+1)">下一页</a></li>
                                            <li :class="currentPage==totalPage?'disabled':''"><a href="javascript:;" @click="turnToPage(totalPage)">尾页</a></li>
                                        </ul>
                                        <div class="go">
                                            <div :class="isPageNumberError?'input-group error':'input-group'">
                                                <input class="form-control" type="number" v-model="goToPage" min="1"><a href="javascript:;" class="input-group-addon" @click="turnToPage(goToPage)">Go</a>
                                            </div>
                                        </div>
                                        <small class="small nowrap"> 当前第 <span class="text-primary" v-text="currentPage"></span> / <span class="text-primary" v-text="totalPage"></span>页，共有 <span class="text-primary" v-text="tt"></span> 条</small>
                                    </div>
                                </div>
                            </div>
                        </section>
                    </div>
                </div>
                <!-- table end -->
            </section>
            <copyright></copyright>
        </section>
    </div>
  </div>
</template>

<script>
import headerGuide from 'components/header-guide.vue'
import sidebar from 'components/sidebar.vue'
import copyright from 'components/copyright.vue'
export default {
  name: 'testProject',
  components: { headerGuide, sidebar, copyright },
  data(){
    return {
        address: "http://10.108.223.23:8080/ATFCloud/",
        testProjectList: [],
        apiUrl: '',
        tt: 0, //总条数
        pageSize: 10, //页面大小
        currentPage: 1, //当前页
        totalPage: 1, //总页数
        listnum: 10, //页面大小
        goToPage: '',
        order: 'id',
        sort: 'asc',
        isPageNumberError: false,
        checkboxModel: [],
        checked: "",
        queryKey: '',
        ids: '',
        //当前选中行
        selectedId: '',
        selectedTestProjectCode: '',
        selectedTestProjectName: '',
        selectedTaskDescription: ''
    }
  },
  mounted(){
        this.getTestProject(this.currentPage, this.pageSize, this.order, this.sort);
        this.changeListNum();
        //全选反选
        $("#chk_all").click(function() {　　
            $("input[name='chk_list']").prop("checked", $(this).prop("checked"));　
        });

        $('.3').addClass('open')
        $('.3 .arrow').addClass('open')
        $('.3-ul').css({display: 'block'})
        $('.3-1').css({color: '#ff6c60'})
  },
  methods:{
      //获取系统
      getTestProject(page, listnum, order, sort) {
          let that=this;
          //获取list通用方法，只需要传入多个所需参数
          $.ajax({
              url: that.address + 'testProjectController/selectAllByPage',
              type: 'GET',
              data: {
                  'page': page,
                  'rows': listnum,
                  'order': order,
                  'sort': sort
              },
              success: function(data) {
                  that.testProjectList = data.rows;
                  that.tt = data.total;
                  that.totalPage = Math.ceil(that.tt / listnum);
                  that.pageSize = listnum;
              }
          });
      },

      //改变页面大小
    changeListNum() {
          let that=this;
          $('#mySelect').change(function() {
              listnum = $(this).children('option:selected').val();
              $("#mySelect").find("option[text='" + listnum + "']").attr("selected", true);
              that.currentPage = 1;
              getTestProject('1', listnum, 'id', 'asc');
          })
      },

      //重新排序
      resort(target) {
          let that=this;
          var spans = target.parentNode.getElementsByTagName("span");
          for (var span in spans) {
              if (spans[span].nodeName === "SPAN") {
                  spans[span].setAttribute("class", "");
              }
          }
          if (target.getAttribute("data-sort") === "desc") {
              that.sort = "asc";
              target.getElementsByTagName("span")[0].setAttribute("class", "icon-sort-up")
              target.setAttribute("data-sort", "asc");
          } else {
              that.sort = "desc";
              target.getElementsByTagName("span")[0].setAttribute("class", "icon-sort-down")
              target.setAttribute("data-sort", "desc");
          }
          that.order = target.getAttribute("data-order");
          that.getTestProject(1, 10, that.order, that.sort);
      },
      //重新排序 结束

      //搜索系统
      queryTestProject() {
          let that=this;
          $.ajax({
              url: that.address + 'testProjectController/selectAllByPage',
              type: 'POST',
              data: {
                  'page': that.currentPage,
                  'rows': that.listnum,
                  'order': that.order,
                  'sort': that.sort,
                  'testProjectCode': that.queryKey
              },
              success: function(data) {
                  that.testProjectList = data.rows;
                  console.log(that.testProjectList)
                  that.tt = data.total;
                  that.totalPage = Math.ceil(that.tt / that.listnum);
                  // that.pageSize = that.listnum;
              }
          });
      },
 
        //获取选中的id
        getIds: function() {
            let that=this;
            var id_array = new Array();
            $('input[name="chk_list"]:checked').each(function() {
                id_array.push($(this).attr('id'));
            });
            that.ids = id_array.join(',');
            // $('input[name="id"]').val(id_array.join(','));
        },
        checkedAll: function() {
            var _this = this;
            console.log(_this.checkboxModel);
            if (this.checked) { //反选
                _this.checkboxModel = [];
            } else { //全选
                _this.checkboxModel = [];
                _this.autList.forEach(function(item) {
                    _this.checkboxModel.push(item.id);
                });
            }
        },
        //turnToPage为跳转到某页
        //传入参数pageNum为要跳转的页数
        turnToPage(pageNum) {
            var ts = this;
            pageNum = parseInt(pageNum);

            //页数不合法则退出
            if (!pageNum || pageNum > ts.totalPage || pageNum < 1) {
                console.log('页码输入有误！');
                ts.isPageNumberError = true;
                return false;
            } else {
                ts.isPageNumberError = false;
            }

            //更新当前页
            ts.currentPage = pageNum;

            //页数变化时的回调
            ts.getTestProject(ts.currentPage, ts.pageSize, 'id', 'asc');
        },

        //添加测试项目
        insert: function() {
            let that=this;
            let testProjectCode=$('#insertForm input[name="testProjectCode"]').val();
            let testProjectName=$('#insertForm input[name="testProjectName"]').val();
            let taskDescription=$('#insertForm textarea[name="taskDescription"]').val();
            if(testProjectCode=='' || testProjectName=='' || taskDescription==''){
                alert("所有项均为必填项");
            }else{
                $.ajax({
                    url: that.address + 'testProjectController/insert',
                    type: 'post',
                    data: $("#insertForm").serializeArray(),
                    success: function(data) {
                        console.info(data);
                        if (data.success) {
                            that.getTestProject(1, app.pageSize, 'id', 'asc');
                            $('#successModal').modal();
                        } else {
                            $('#failModal').modal();
                        }
                    },
                    error: function() {
                        $('#failModal').modal();
                    }
                });
            }
        },
        //删除测试项目
        del: function() {
            this.getIds();
            console.log(app.ids)
            let that=this;
            $.ajax({
                url: that.address + 'testProjectController/delete',
                type: 'post',
                data: {
                    'ids': that.ids
                },
                success: function(data) {
                    console.info(data);
                    if (data.success) {
                        that.getTestProject(1, that.pageSize, 'id', 'asc');
                        $('#successModal').modal();
                    } else {
                        $('#failModal').modal();
                    }
                },
                error: function() {
                    $('#failModal').modal();
                }
            });
        },
        //修改测试项目
        update: function() {
            let that=this;
            $.ajax({
                url: that.address + 'testProjectController/update',
                type: 'post',
                data: $("#updateForm").serializeArray(),
                success: function(data) {
                    console.info(data);
                    if (data.success) {
                        that.getTestProject(1, that.pageSize, 'id', 'asc');
                        $('#successModal').modal();
                    } else {
                        $('#failModal').modal();
                    }
                },
                error: function() {
                    $('#failModal').modal();
                }
            });
        },
        //获取当前选中行内容
        getSelected: function() {
            var selectedInput = $('input[name="chk_list"]:checked');
            var selectedId = selectedInput.attr('id');
            $('input[name="id"]').val(selectedId);
            $('#updateForm input[name="testProjectCode"]').val(selectedInput.parent().next().html());
            $('#updateForm input[name="testProjectName"]').val(selectedInput.parent().next().next().html());
            $('#updateForm textarea[name="taskDescription"]').val(selectedInput.parent().next().next().next().html());
        },
        //进入
        to: function() {
            var selectedInput = $('input[name="chk_list"]:checked');
            if (selectedInput.length === 0) {
                $('#selectAlertModal').modal();
            } else {
                var caselibId = selectedInput.parent().next().next().next().next().html();
                //存储测试项目id到sessionstorage
                sessionStorage.setItem("caselibid", caselibId);
                location.href = "caseManagement.html";
            }
        }
  }
}
</script>

<style>
  @import '../../assets/css/base.scss';
</style>