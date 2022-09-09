<template class="container">
    <div class="header">
        <div class="header__left">
            <div class="header__sibar"></div>
            <div class="header__logo"></div>
        </div>
        <div class="header__right">
            <div>
                <select name="" id="">
                    <option value="1">Nhà hàng hải sản Biển Đông</option>
                    <option value="1">Nhà hàng Hoàng Mai</option>
                </select>
            </div>
            <div class="user">
                <div class="user__name">Nguyễn Văn Mạnh</div>
                <div class="user__avatar"></div>
            </div>
        </div>
    </div>

    <div class="main">
            <div class="menu">
                <div class="menu__item">
                    <div class="menu__icon icon icon-16 icon__dashboard"></div>
                    <div class="menu__text">Danh sách nhân viên</div>
                </div>
                <div class="menu__item">
                    <div class="menu__icon icon icon-16 icon__employee"></div>
                    <div class="menu__text">Danh sách khách hàng</div>
                </div>
                <div class="menu__item">
                    <div class="menu__icon icon icon-16 icon__report"></div>
                    <div class="menu__text">Báo cáo</div>
                </div>
            </div>
            <div class="content">
                <div class="page__header">
                    <div class="page__header--title heading">Danh sách nhân viên</div>
                    <button id="btnAdd" class="page__header--button button button__icon button__icon--employee">Thêm mới nhân viên</button>
                </div>
                <div class="page__toolbar">
                    <div class="page__toolbar--left">
                        <input type="text" class="input input__icon input__icon--search">
                    </div>
                    <div class="page__toolbar--right">
                        <button id="btnDelete"></button>
                        <button id="btnDuplicate"></button>
                        <button id="btnRefresh"></button>
                    </div>
                </div>
                <div class="page__table">
                    <div class="table__content">
                        <table id="tbEmployeeList" class="table">
                            <thead>
                                <tr>
                                    <th class="text-align--left" title="Số thứ tự" style="width:50px">STT</th>
                                    <th class="text-align--left" style="width:100px">Mã nhân viên</th>
                                    <th class="text-align--left">Họ và tên</th>
                                    <th class="text-align--left" style="width:50px">Giới tính</th>
                                    <th class="text-align--center" style="width:100px">Ngày sinh</th>
                                    <th class="text-align--left" style="width:100px">Điện thoại</th>
                                    <th class="text-align--left" style="width:150px">Email</th>
                                    <th class="text-align--left" style="width:200px">Vị trí</th>
                                    <th class="text-align--left" style="width:200px">Phòng ban</th>
                                    <th class="text-align--right" style="width:150px">Mức lương cơ bản</th>
                                    <th class="text-align--left" style="width:150px">Tình trạng công việc</th>
                                </tr>
                            </thead>
                            <tbody>

                            </tbody>
                        </table>
                    </div>
                    <div class="table__paging">
                        <div class="table__paging--left">
                            Hiển thị <b>01-10/200</b> nhân viên
                        </div>
                        <div class="table__paging--center">
                            <button class="paging__button paging__button--first"></button>
                            <button class="paging__button paging__button--prev"></button>
                            <div class="paging__button--group">
                                <button class="paging__number">1</button>
                                <button class="paging__number">2</button>
                                <button class="paging__number paging__number--selected">3</button>
                                <button class="paging__number">4</button>
                                <button class="paging__number">5</button>
                                <button class="paging__number">6</button>
                            </div>
                            <button class="paging__button paging__button--next"></button>
                            <button class="paging__button paging__button--last"></button>
                        </div>
                        <div class="table__paging--right">
                            <select name="" class="combobox">
                                <option value="10">10 nhân viên/ trang</option>
                                <option value="20">10 nhân viên/ trang</option>
                                <option value="30">10 nhân viên/ trang</option>
                                <option value="40">10 nhân viên/ trang</option>
                            </select>
                        </div>
                    </div>
                </div>
            </div>
        </div>
</template>
  
  <script>
import axios from 'axios';

  export default {
    name: 'ProjectNew',
    props: {
    },
    // call api 
    created() {
    axios.get('https://cukcuk.manhnv.net/api/v1/Employees')
    .then(response => {
      this.posts = response.data
      console.log(">>>>>",response);
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
  }
  </script>


<style scoped>
    .heading {
    font-family: MISA Font Bold;
    font-size: 24px;
}
    .menu {
    width: 225px;
    flex-shrink: 225px;
    display: flex;
    flex-direction: column;
    border-right: 1px solid #ccc;
    box-sizing: border-box;
}

.menu__item {
    display: flex;
    align-items: center;
    padding-left: 16px;
    height: 40px;
    width: 100%;
    cursor: pointer;
}

.menu__item:hover {
    background-color: #e5e5e5;
}

.menu__icon {
    width: 16px;
    height: 16px;
}

.menu__text {
    margin-left: 10px;
}
    .user {
    display: flex;
    align-items: center;
}

.user__name {
    font-weight: 700;
}

.user__avatar {
    width: 32px;
    height: 32px;
    /* background-image: url(../../assets/icon/avatar-default.png); */
    background-position: center;
    background-size: 32px;
    background-size: contain;
    margin-left: 10px;
}
    .paging__number {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-basis: 40px;
    margin: 0 4px;
    cursor: pointer;
    border: 1px solid #dedede;
    background-color: #fff;
}

.paging__number:hover {
    background-color: #dedede;
}

.paging__number--selected {
    background-color: #019160;
    color: #fff;
}
    .paging__button--group {
    display: flex;
    align-items: center;
    justify-content: center;
}
    .table__paging {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 56px;
    border-top: 1px solid #ccc
}

.table__paging--center {
    display: flex;
    align-items: center;
}
    .page__table {
    display: flex;
    flex-direction: column;
    align-content: stretch;
    /* background-color: aqua; */
    flex: 1;
    justify-content: space-between;
}
    .page__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-sizing: border-box;
}
.page__toolbar {
    display: flex;
    justify-content: space-between;
    box-sizing: border-box;
    align-items: center;
    margin: 4px 0;
}
    .content {
    display: flex;
    flex-direction: column;
    flex: 1;
    padding: 24px;
    box-sizing: border-box;
    border-top: 1px solid #ccc;
    /* background-color: #e9ebee; */
}
    .container {
    display: flex;
    flex-direction: column;
}
    .main {
    display: flex;
    flex-direction: row;
    height: calc(100vh - 50px);
    width: 100%;
}
    .header {
    display: flex;
    grid-column-start: 1;
    grid-column-end: 3;
    height: 50px;
    box-sizing: border-box;
}

.header__left {
    width: 225px;
    height: 100%;
    display: flex;
    align-items: center;
    padding-left: 16px;
    box-sizing: border-box;
    border-right: 1px solid #ccc;
}

.header__sibar {
    width: 24px;
    height: 24px;
    /* background-image: url(../../assets/img/toggle.png); */
    background-repeat: no-repeat;
    background-size: 24px 24px;
}

.header__logo {
    margin-left: 10px;
    flex: 1;
    height: 24px;
    /* background-image: url(../../assets/cukcuk-logo.png); */
    background-repeat: no-repeat;
    background-size: contain;
}

.header__right {
    box-sizing: border-box;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex: 1;
    padding: 0 24px;
    height: 100%;
}
</style>
