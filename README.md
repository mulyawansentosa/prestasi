# Prestasi

[![Join the chat at https://gitter.im/prestasi/Lobby](https://badges.gitter.im/prestasi/Lobby.svg)](https://gitter.im/prestasi/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/bantenprov/prestasi/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/bantenprov/prestasi/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/bantenprov/prestasi/badges/build.png?b=master)](https://scrutinizer-ci.com/g/bantenprov/prestasi/build-status/master)
[![Latest Stable Version](https://poser.pugx.org/bantenprov/prestasi/v/stable)](https://packagist.org/packages/bantenprov/prestasi)
[![Total Downloads](https://poser.pugx.org/bantenprov/prestasi/downloads)](https://packagist.org/packages/bantenprov/prestasi)
[![Latest Unstable Version](https://poser.pugx.org/bantenprov/prestasi/v/unstable)](https://packagist.org/packages/bantenprov/prestasi)
[![License](https://poser.pugx.org/bantenprov/prestasi/license)](https://packagist.org/packages/bantenprov/prestasi)
[![Monthly Downloads](https://poser.pugx.org/bantenprov/prestasi/d/monthly)](https://packagist.org/packages/bantenprov/prestasi)
[![Daily Downloads](https://poser.pugx.org/bantenprov/prestasi/d/daily)](https://packagist.org/packages/bantenprov/prestasi)

Prestasi

### Install via composer

- Development snapshot

```bash
$ composer require bantenprov/prestasi:dev-master
```

- Latest release:

```bash
$ composer require bantenprov/prestasi
```

### Download via github

```bash
$ git clone https://github.com/bantenprov/prestasi.git
```

#### Edit `config/app.php` :

```php
'providers' => [

    /*
     * Package Service Providers...
     */
    Laravel\Tinker\TinkerServiceProvider::class,
    //....
    Bantenprov\Prestasi\PrestasiServiceProvider::class,
```

#### Publish vendor :

```bash
$ php artisan vendor:publish --tag=prestasi-seeds
$ php artisan vendor:publish --tag=prestasi-assets
$ php artisan vendor:publish --tag=prestasi-public
```

#### Lakukan auto dump :

```bash
$ composer dump-autoload
```

#### Lakukan migrate :

```bash
$ php artisan migrate
```

#### Lakukan seeding :

```bash
$ php artisan db:seed --class=BantenprovPrestasiSeeder
```

#### Tambahkan route di dalam file : `resources/assets/js/routes.js` :

```javascript
{
    path: '/dashboard',
    redirect: '/dashboard/home',
    component: layout('Default'),
    children: [
        //== ...
        {
            path: '/dashboard/prestasi',
            components: {
                main: resolve => require(['./components/views/bantenprov/prestasi/DashboardPrestasi.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "Prestasi"
            }
        },
        //== ...
    ]
},
```

```javascript
{
    path: '/admin',
    redirect: '/admin/dashboard/home',
    component: layout('Default'),
    children: [
        //== ...
        {
            path: '/admin/prestasi',
            components: {
                main: resolve => require(['./components/bantenprov/prestasi/Prestasi.index.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "Prestasi"
            }
        },
        {
            path: '/admin/prestasi/create',
            components: {
                main: resolve => require(['./components/bantenprov/prestasi/Prestasi.add.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "Add Prestasi"
            }
        },
        {
            path: '/admin/prestasi/:id',
            components: {
                main: resolve => require(['./components/bantenprov/prestasi/Prestasi.show.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "View Prestasi"
            }
        },
        {
            path: '/admin/prestasi/:id/edit',
            components: {
                main: resolve => require(['./components/bantenprov/prestasi/Prestasi.edit.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "Edit Prestasi"
            }
        },
        //== ...
    ]
},
```
#### Edit menu `resources/assets/js/menu.js`

```javascript
{
    name: 'Dashboard',
    icon: 'fa fa-dashboard',
    childType: 'collapse',
    childItem: [
        //== ...
        {
            name: 'Prestasi',
            link: '/dashboard/prestasi',
            icon: 'fa fa-angle-double-right'
        },
        //== ...
    ]
},
```

```javascript
{
    name: 'Admin',
    icon: 'fa fa-lock',
    childType: 'collapse',
    childItem: [
        //== ...
        {
            name: 'Prestasi',
            link: '/admin/prestasi',
            icon: 'fa fa-angle-double-right'
        },
        //== ...
    ]
},
```

#### Tambahkan components `resources/assets/js/components.js` :

```javascript
import Prestasi from './components/bantenprov/prestasi/Prestasi.chart.vue';
Vue.component('echarts-prestasi', Prestasi);

import PrestasiKota from './components/bantenprov/prestasi/PrestasiKota.chart.vue';
Vue.component('echarts-prestasi-kota', PrestasiKota);

import PrestasiTahun from './components/bantenprov/prestasi/PrestasiTahun.chart.vue';
Vue.component('echarts-prestasi-tahun', PrestasiTahun);

import PrestasiAdminShow from './components/bantenprov/prestasi/PrestasiAdmin.show.vue';
Vue.component('admin-view-prestasi-tahun', PrestasiAdminShow);

//== Echarts Angka Partisipasi Kasar

import PrestasiBar01 from './components/views/bantenprov/prestasi/PrestasiBar01.vue';
Vue.component('prestasi-bar-01', PrestasiBar01);

import PrestasiBar02 from './components/views/bantenprov/prestasi/PrestasiBar02.vue';
Vue.component('prestasi-bar-02', PrestasiBar02);

//== mini bar charts
import PrestasiBar03 from './components/views/bantenprov/prestasi/PrestasiBar03.vue';
Vue.component('prestasi-bar-03', PrestasiBar03);

import PrestasiPie01 from './components/views/bantenprov/prestasi/PrestasiPie01.vue';
Vue.component('prestasi-pie-01', PrestasiPie01);

import PrestasiPie02 from './components/views/bantenprov/prestasi/PrestasiPie02.vue';
Vue.component('prestasi-pie-02', PrestasiPie02);

//== mini pie charts
import PrestasiPie03 from './components/views/bantenprov/prestasi/PrestasiPie03.vue';
Vue.component('prestasi-pie-03', PrestasiPie03);
```
