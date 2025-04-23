# TIWAEI-TRANSPORTSERVICE
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";

export default function Home() {
  const [loads, setLoads] = useState([]);
  const [form, setForm] = useState({ from: "", to: "", description: "" });

  const handlePostLoad = () => {
    if (!form.from || !form.to) return;
    setLoads([...loads, form]);
    setForm({ from: "", to: "", description: "" });
  };

  return (
    <div className="p-4 space-y-6">
      <h1 className="text-3xl font-bold text-center">Tiwari Transport Service</h1>
      <p className="text-center text-gray-600">Truck Load Posting and Transport Services</p>

      <Card>
        <CardContent className="p-4 space-y-4">
          <h2 className="text-xl font-semibold">Post a Load</h2>
          <Input
            placeholder="From (City/State)"
            value={form.from}
            onChange={(e) => setForm({ ...form, from: e.target.value })}
          />
          <Input
            placeholder="To (City/State)"
            value={form.to}
            onChange={(e) => setForm({ ...form, to: e.target.value })}
          />
          <Textarea
            placeholder="Load Description"
            value={form.description}
            onChange={(e) => setForm({ ...form, description: e.target.value })}
          />
          <Button onClick={handlePostLoad}>Post Load</Button>
        </CardContent>
      </Card>

      <div>
        <h2 className="text-xl font-semibold mb-2">Posted Loads</h2>
        <div className="space-y-2">
          {loads.map((load, idx) => (
            <Card key={idx}>
              <CardContent className="p-4">
                <p><strong>From:</strong> {load.from}</p>
                <p><strong>To:</strong> {load.to}</p>
                <p><strong>Description:</strong> {load.description}</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </div>
    </div>
  );
}
