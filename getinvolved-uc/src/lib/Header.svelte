<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.2/font/bootstrap-icons.css"
/>

<script>
    import logo from '../assets/image.png'
</script>

<div class="header">
    <div>
        <img src={logo} class="logo"/>
    </div>
    <i class="bi bi-person-circle user-icon"></i>
</div>

<style>
.header {
    position: fixed;
    width: 100vw;
    height: 80px;
    background-color: white;
    border-bottom-style: solid;
    border-bottom-color: lightgrey;
    border-bottom-width: 2px;
}

.user-icon {
    font-size: 40px;
    position: absolute;
    right: 0;
    top: 0;
    padding-top: 20px;
    padding-right: 20px;
}

.logo {
    height: 50px;
    margin-top: 15px;
    margin-left: 15px;
}

</style>
