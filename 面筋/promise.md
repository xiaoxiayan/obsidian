```
class myPromise {

  static PENDING = '待定'

  static FULFILLD = '成功'

  static REJECTED = '拒绝'

  status

  result

  resQueue

  rejQueue

  constructor(fn) {

    this.status = myPromise.PENDING

    this.result = null

    this.resQueue = []

    this.rejQueue = []

    try {

      fn(this.resolve.bind(this), this.reject.bind(this))

    } catch (error) {

      this.reject(error)

    }

  }

  

  resolve(result) {

    setTimeout(() => {

      if (this.status === myPromise.PENDING) {

        this.status = myPromise.FULFILLD

        this.result = result

        this.resQueue.forEach((callback) => {

          callback(result)

        })

      }

    })

  }

  

  reject(result) {

    setTimeout(() => {

      if (this.status === myPromise.PENDING) {

        this.status = myPromise.REJECTED

        this.result = result

        this.rejQueue.forEach(callback => {

          callback(result)

        })

      }

    })

  }

  

  then(onFULFILLD) {

    return new myPromise((res, rej) => {

      onFULFILLD = typeof onFULFILLD === 'function' ? onFULFILLD : () => { }

      // 如果这个时候 promise 中执行的异步行为， then 会比 异步行为先执行， 白跑一躺， 所以，当执行到then的时候。判断状态，如果状态是 等待， 那么把函数存起来在 res, rej 函数中再调用

      if (this.status === myPromise.PENDING) {

  

        this.resQueue.push(onFULFILLD)

  

        if (res) {

          this.resQueue.push(res)

        }

        if (rej) {

          this.rejQueue.push(rej)

        }

      }

  

      if (this.status === myPromise.FULFILLD) {

        setTimeout(() => {

          onFULFILLD(this.result)

        })

      }

  
  

    })

  
  

  }

  catch(onREJECTED) {

    return new myPromise((res, rej) => {

      onREJECTED = typeof onREJECTED === 'function' ? onREJECTED : () => { }

      if (this.status === myPromise.PENDING) {

        this.rejQueue.push(onREJECTED)

  

        if (res) {

          this.resQueue.push(res)

        }

        if (rej) {

          this.rejQueue.push(rej)

        }

      }

  

      if (this.status === myPromise.REJECTED) {

        setTimeout(() => {

          onREJECTED(this.result)

        })

      }

    })

  }

}

  

// function fff() {

//   return new myPromise((res, rej) => {

//     setTimeout(() => {

//       console.log(1111)

//       res('resfff')

//     }, 1000)

//   })

// }

  

// async function getfff() {

//   const res = await fff()

//   console.log('getfff--', res)

// }

  

// function fffthen() {

//   fff().then((res) => {

//     console.log(res)

//   })

// }

  

// getfff()

// fffthen()

  
  

console.log(1)

let promise = new myPromise((resolve, reject) => {

  console.log(2)

  setTimeout(() => {

    reject('最后执行')

    console.log(4)

  })

})

  

promise.catch(

  result => { console.log(result) },

  result => { console.log('rej===>', result.message) },

).catch(

  result => { console.log('ddd--', result) },

).catch(

  result => { console.log('aaafa a', result) },

)

console.log(3)
```