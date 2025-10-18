// SilverShopApp.jsx
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

const products = [
  {
    id: 1,
    name: "انگشتر نقره قلبی",
    price: 850000,
    image: "https://example.com/ring.jpg",
  },
  {
    id: 2,
    name: "گردنبند طرح ماه",
    price: 1250000,
    image: "https://example.com/necklace.jpg",
  },
  {
    id: 3,
    name: "دستبند ظریف نقره",
    price: 950000,
    image: "https://example.com/bracelet.jpg",
  },
];

export default function SilverShopApp() {
  const [cart, setCart] = useState([]);

  const addToCart = (item) => {
    setCart([...cart, item]);
  };

  const total = cart.reduce((sum, item) => sum + item.price, 0);

  return (
    <div className="min-h-screen bg-gray-50 p-6">
      <h1 className="text-3xl font-bold text-center mb-6 text-gray-800">
        🩶 نایب گالری | نقره‌های خاص شما
      </h1>

      <div className="grid grid-cols-1 sm:grid-cols-3 gap-6">
        {products.map((item) => (
          <Card key={item.id} className="shadow-lg hover:scale-105 transition">
            <img
              src={item.image}
              alt={item.name}
              className="w-full h-56 object-cover rounded-t-2xl"
            />
            <CardContent className="p-4 text-center">
              <h2 className="text-lg font-semibold">{item.name}</h2>
              <p className="text-gray-600">{item.price.toLocaleString()} تومان</p>
              <Button className="mt-3 w-full" onClick={() => addToCart(item)}>
                افزودن به سبد خرید
              </Button>
            </CardContent>
          </Card>
        ))}
      </div>

      <div className="mt-8 bg-white p-4 rounded-2xl shadow-md max-w-md mx-auto">
        <h2 className="text-xl font-bold text-gray-700 mb-3">🛒 سبد خرید</h2>
        {cart.length === 0 ? (
          <p className="text-gray-500">سبد خرید شما خالی است.</p>
        ) : (
          <>
            {cart.map((item, index) => (
              <p key={index}>
                {item.name} — {item.price.toLocaleString()} تومان
              </p>
            ))}
            <hr className="my-2" />
            <p className="font-semibold">جمع کل: {total.toLocaleString()} تومان</p>
            <Button className="mt-3 w-full">ثبت سفارش</Button>
          </>
        )}
      </div>
    </div>
  );
}![IMG_20251008_010035_821](https://github.com/user-attachments/assets/4b060c32-a9db-4031-baca-0f1ddbf66b39)
